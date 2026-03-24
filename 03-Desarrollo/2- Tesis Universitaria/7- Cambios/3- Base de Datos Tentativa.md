
@startuml
skinparam classAttributeIconSize 0

class Usuario {
    +id_usuario: Integer [PK]
    +nombre_completo: String
    +usuario: String [UNIQUE]
    +contrasena_hash: String
    +rol: String [secretaria, medico, admin]
    +activo: Boolean
    +created_at: DateTime
    +updated_at: DateTime
}

class Medico {
    +id_medico: Integer [PK]
    +id_usuario: Integer [FK]
    +especialidad: String
    +created_at: DateTime
}

class Paciente {
    +id_paciente: Integer [PK]
    +nombre_completo: String
    +cedula: String [UNIQUE]
    +telefono: String
    +fecha_nacimiento: Date
    +sexo: String [M, F]
    +direccion: Text
    +created_at: DateTime
    +updated_at: DateTime
}

class Cita {
    +id_cita: Integer [PK]
    +id_paciente: Integer [FK]
    +id_medico: Integer [FK]
    +fecha: Date
    +hora: Time
    +estado: String [programada, completada, cancelada]
    +motivo_consulta: Text
    +notas_secretaria: Text
    +created_at: DateTime
    +updated_at: DateTime
}

class NotaMedica {
    +id_nota: Integer [PK]
    +id_cita: Integer [FK]
    +descripcion: Text
    +fecha_registro: DateTime
}

class DisponibilidadMedica {
    +id_disponibilidad: Integer [PK]
    +id_medico: Integer [FK]
    +dia_semana: String [lunes-domingo]
    +hora_inicio: Time
    +hora_fin: Time
}

class AuditoriaLog {
    +id_log: Integer [PK]
    +id_usuario: Integer [FK]
    +accion: String [crear, modificar, eliminar, reporte]
    +tabla_afectada: String
    +registro_id: Integer
    +fecha_accion: DateTime
}

' Relaciones
Usuario "1" -- "0..1" Medico : es >
Usuario "1" -- "*" AuditoriaLog : registra >
Medico "1" -- "*" DisponibilidadMedica : tiene >
Medico "1" -- "*" Cita : atiende >
Paciente "1" -- "*" Cita : solicita >
Cita "1" -- "0..1" NotaMedica : genera >

@enduml