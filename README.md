# Python
Introducción a la línea de comando y a la programación para análisis bioinformáticos
Teórico y práctico


# Códigos utilizados

## Ejercicios o ejemplos teóricos


**EXTRAER CARACTERES DE UN STRING**

    dna = 'AGCTAGCATCGATCGATCTAGCTAGCT'
    print dna[0:3]
    print dna[-3:]
    print dna[3:9]
    print dna[:-3]


**SALIDO DE DATOS EN PANTALLA**

	print '\n'
	print 'In the town where I was born lived a man who sailed the sea'
	print 'And he told us of his life\nIn the land of submarines\n'
	frase_1 = '\tWe all live in '
	frase_2 = '\ta yellow submarine '
	print frase_1 + frase_2
	print frase_2 * 2
	print '\n'

**INGRESO DE DATOS POR EL USUARIO**

  print 'Ingrese los datos solicitados '
  nombre = raw_input('Cual es tu nombre: ')
  edad = input('Cual es su edad: ')
  color = raw_input('Y su comida preferida: ')

  print nombre, 'tiene\n', edad, 'anhos y \tco\tme ', color

**SCRIPT PARA SABER SI UN NUMERO ES CERO, PAR O IMPAR**

  numero = input('Numero: ')
  if numero == 0:
    print 'El numero es cero'
  elif numero % 2 == 0:
    print 'El numero es par'
  else:
    print 'El numero es impar'


**SCRIPT PARA ADIVINAR UN NUMERO RANDOM**

  import random
  num = random.randint(1, 10)

  adivino = False
  while not adivino:
    num_guess = input('Adinvina, un numero del 1 al 10: ')
    if num_guess != num:
      print 'No adivinaste, intenta de nuevo'
    else:
      adivino = True
      print 'Adivinaste! el numero era: ', num
    
**DOS OPCIONES DE SUMAR LOS ELEMENTOS DE UNA LISTA**

  total = 0

  for numero in range(1, 11):
    total = total + papa
    print total

  total = 0

  lista = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

  for numero in lista:
    total = total + papa
    print total

**DOS OPCIONES PARA HACER UNA CUENTA REGRESIVA DESDE 10 a 0**

  numero = 10

  while numero>=0:
    print numero
    numero = numero -1

  for i in range(0,numero+1):
    print numero-i


**ESCRIBIR UNA SENTENCIA EN UN ARCHIVO NUEVO**

  f = open('file.txt', 'w') 
  f.write('ACTGATAGCTAGACTATGCA')  
  f.close()


**CALCULO DE CONTENIDO GC**

  lista_secuencias = ['ACGATAGCTAGC', 'TAGCTAGCTAGCTAGCTA', 'ATCGATCGATAGC', 'ATCGATCGATCGATG', 'TATCGATCGATTAG']

  for sec in lista_secuencias:
      largo = len(sec)
      cant_c = sec.count('C')
      cant_G = sec.count('G')
      porcentaje_GC = (float(cant_c + cant_G)/largo) * 100	#cambio el tipo de dato a int a float
      print sec, porcentaje_GC, '%'


**DOS OPCIONES PARA CALCULAR EL LARGO DE UNA CADENA DE CARACTERES**

  largo = 0
  for letra in cadena:
    largo = largo + 1
  print largo

  cadena = 'ACGCAGCATAGCTACTATCAGCTAATCGACCGCTAGCAG'
  largo = len(cadena)
  print largo


**DOS OPCIONES PARA CALCULAR EL LARGO DE UNA CADENA DE CARACTERES**

  cadena = 'ACGCAGCATAGCTACTATCAGCTAATCGACCGCTAGCAG'

  cantidad_A = cadena.count('A')
  print cantidad_A

  cantidad_A = 0
  for letra in cadena:
    if letra == 'A':
      cantidad_A = cantidad_A + 1
  print cantidad_A

**DOS OPCIONES PARA CALCULAR LA RAIZ CUADRADA DE UN NUMERO**

  x= 2
  raiz = x**0.5
  print raiz

  import math
  x= 2
  raiz = math.sqrt(x)
  print raiz

## Ejercicios prácticos

**EJERCICIO 1 - POR PASOS**

  print 'Programa para calcular el contenido GC de una secuencia'

  lista_secuencias = ['ACGATAGCTAGC', 'TAGCGAGCTAGCTAGCTC', 'ATCGATCGATAGC', 'ATCGATCGATCGATG', 'TATCGATCGATTAG']

  for secuencia in lista_secuencias:
    print secuencia

  for secuencia in lista_secuencias:
    if len(secuencia) >= 15:
      print secuencia

  for secuencia in lista_secuencias:
    if len(secuencia) >= 15:
      largo = len(secuencia)
      cant_C = secuencia.count('C')
      cant_G = secuencia.count('G')
      porcentaje_GC = (float(cant_C + cant_G) / largo) * 100
      if porcentaje_GC < 50:
        print secuencia, porcentaje_GC, '%'


**EJERCICIO 2** 

**Para un archivo**

  import sys
  archivo = sys.argv[1]	#Este archivo tengo que indicarlo por linea de comando

  nuevo_archivo = open('lista_datos.txt','w') 

  for linea in open(archivo, 'r'):
    if linea.startswith('>'):
      ID = linea.split('|')[3]
      genero = linea.split('|')[4].split(' ')[1]
      especie = linea.split('|')[4].split(' ')[2]
      nuevo_archivo.write(ID + '\t' + genero + '\t' + especie + '\n')
  nuevo_archivo.close() 

**Para varios archivos**

  import sys

  file1 = sys.argv[1]
  file2 = sys.argv[2]

  files = [open(file1, 'r'), open(file2, 'r')]

  numerador = 1

  for cada_file in files:
    archivo_nuevo = open(str(numerador) + '.txt', 'w') #str es porque tengo que pasar de tipo numerico a tipo string
    numerador = numerador + 1
    for linea in cada_file:
      if linea.startswith('>'):
        ID = linea.split('|')[3]
        todo_especie = linea.split('|')[4]
        genero = todo_especie.split(' ')[1]
        especie = todo_especie.split(' ')[2]
        #archivo_nuevo.write(ID + '\t' + genero + '\t' + especie + '\n')
    archivo_nuevo.close()
