
---

### 🔧 1. **Configura tu entorno de desarrollo**

#### Requisitos:

- Python en su ultima versión+
- VS Code o PyCharm
- Git (para control de versiones)


#### Instala dependencias:

```bash
pip install flask flask_sqlalchemy flask_login
```

---

### 📁 2. **Estructura básica del proyecto**

```bash
citas_hospital/
│
├── app/
│   ├── __init__.py       # Configuración Flask y base de datos
│   ├── models.py         # Definición de tablas (Paciente, Cita, Usuario, etc.)
│   ├── routes/
│   │   ├── auth.py       # Login/Logout
│   │   ├── citas.py      # Crear, editar, cancelar citas
│   │   └── dashboard.py  # Pantalla principal por rol
│   ├── templates/        # HTML con Jinja2
│   └── static/           # CSS, JS y Bootstrap
│
├── run.py                # Archivo principal para iniciar el servidor
└── config.py             # Configuración general (BD, claves, etc.)
```

---

### 🛠 3. **Crea el archivo `__init__.py`**

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
from flask_login import LoginManager

db = SQLAlchemy()
login_manager = LoginManager()

def create_app():
    app = Flask(__name__)
    app.config['SECRET_KEY'] = 'clave-secreta'
    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///hospital.db'
    
    db.init_app(app)
    login_manager.init_app(app)

    # Importar blueprints
    from .routes.auth import auth_bp
    from .routes.citas import citas_bp
    from .routes.dashboard import dashboard_bp
    app.register_blueprint(auth_bp)
    app.register_blueprint(citas_bp)
    app.register_blueprint(dashboard_bp)

    return app
```

---

### 🔍 4. **Crea los modelos (`models.py`)**

Ejemplo básico:

```python
from . import db
from flask_login import UserMixin

class Usuario(UserMixin, db.Model):
    id = db.Column(db.Integer, primary_key=True)
    nombre = db.Column(db.String(100))
    rol = db.Column(db.String(50))  # 'secretaria' o 'medico'
    username = db.Column(db.String(50), unique=True)
    password = db.Column(db.String(100))

class Paciente(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    nombre = db.Column(db.String(100))
    cedula = db.Column(db.String(15))
    telefono = db.Column(db.String(20))

class Cita(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    paciente_id = db.Column(db.Integer, db.ForeignKey('paciente.id'))
    medico_id = db.Column(db.Integer, db.ForeignKey('usuario.id'))
    fecha = db.Column(db.Date)
    hora = db.Column(db.Time)
    estado = db.Column(db.String(20))  # "pendiente", "cancelada", "completada"
```

---

### 🌐 5. **Configura el servidor (`run.py`)**

```python
from app import create_app

app = create_app()

if __name__ == '__main__':
    app.run(debug=True)
```

---

### 🧪 6. **Inicializa la base de datos**

Desde un terminal:

```bash
python
>>> from app import create_app, db
>>> app = create_app()
>>> app.app_context().push()
>>> db.create_all()
```

---

### 🎨 7. **Diseña el Frontend**

Utiliza Bootstrap y HTML dentro de `templates/` con bloques como:

```html
<!-- templates/layout.html -->
<!doctype html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <link rel="stylesheet" href="{{ url_for('static', filename='bootstrap.min.css') }}">
  <title>{% block title %}Sistema de Citas{% endblock %}</title>
</head>
<body>
  <div class="container mt-4">
    {% block content %}{% endblock %}
  </div>
</body>
</html>
```

---

### ✅ Próximos pasos:

1. Login y autenticación con roles (Flask-Login)
    
2. CRUD de citas (crear, modificar, cancelar)
    
3. Vista para secretarias y otra para médicos
    
4. Reportes básicos y filtros por fecha
    

---

