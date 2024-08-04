# Python Regex

## compile
pattern = re.compite(r'\d+')	cargar una regex en el objeto patrón. Es util si la regex se va a usar varias veces en el script

## match
re.match(pattern, 'string')	devuelve True si hay coincidencia del patrón al inicio de la cadena, de lo contrario devuelve None
match.group()			extraer información dentro de una cadena


match.start()			devuelve el índice de la coincidencia
match.end()			devuelve el índice final de la coincidencia
match.span()			devuelve una tupla con los índices inicial y final de la coincidencia


## search
re.search(pattern, 'aquí va la cadena, flags = 0)	busca el patrón en toda la cadena

# Ejemplos:
## match
	import re

	# Definimos el patrón para una dirección de correo electrónico básica
	pattern = r'(\w+)@(\w+)\.(\w+)'

	# Cadena a verificar
	email = 'usuario@dominio.com'

	# Usamos re.match() para verificar si la cadena coincide con el patrón
	match = re.match(pattern, email)

	if match:
	    	print("El correo electrónico es válido.")
	    	print("Usuario:", match.group(1))  # usuario
	    	print("Dominio:", match.group(2))  # dominio
	    	print("Extensión:", match.group(3))  # com
	    else:
	    	print("El correo electrónico no es válido.")


## match.group()
	import re

	pattern = r'(\d+)-(\d+)-(\d+)'
	string = 'Primera fecha: 2024-07-05, Segunda fecha: 2025-08-06.'

	matches = re.finditer(pattern, string)
	for match in matches:
	    print(match.group(1))  # 2024, luego 2025
	    print(match.group(2))  # 07, luego 08
	    print(match.group(3))  # 05, luego 06
