# TP2 - Algoritmos y Programación I

Trabajo Práctico 2 para la materia Algoritmos y Programación I (Cátedra Essaya) de la Facultad de Ingeniería de la Universidad de Buenos Aires.

Cursada el primer cuatrimestre del 2018.

######################################################################################################################

TP2 - Generador de crucigramas
Consigna
El objetivo del trabajo práctico es implementar un generador de crucigramas simples.

Entrada
Se dispone de un archivo palabras.csv con el siguiente formato:

palabra|definicion
A partir de dicho archivo el programa debe seleccionar un conjunto de palabras al azar (uno distinto cada vez que se ejecuta) y generar un crucigrama.

Crucigrama
El crucigrama generado debe cumplir con las siguientes condiciones:

Debe tener una sola palabra horizontal, de al menos 8 letras.
No puede haber dos letras consecutivas en la palabra horizontal que se crucen con una vertical.
No puede haber tres letras consecutivas en la palabra horizontal que no se crucen con ninguna vertical.
Todas las palabras deben ser diferentes.
Nota: el cruce entre palabras es, por supuesto, en una letra compartida. Por simplicidad, vamos a considerar a todas las letras con tilde, virgulilla o similar como diferentes a las letras simples. Es decir que los caracteres A y Á son diferentes, como así también N y Ñ, U y Ü, etc. Por lo tanto, la palabra ÁTICO no puede cruzarse con BANANA, pero sí con ANANÁ.

Salida
El programa debe imprimir un crucigrama listo para ser jugado, mostrando las celdas del crucigrama vacías, la referencia de coordenadas de las celdas y las definiciones de cada palabra.

Se deja a libre elección el formato en el que se muestra cada elemento, pero se sugiere un ejemplo a continuación.

Si el programa recibe la opción -s (ejemplo: python tp2.py -s), además debe imprimir la solución del crucigrama.

Ejemplo
Si el archivo palabras.csv contiene, entre otras, las siguientes palabras:

NÓSTICO|Relativo a la mezcla esencial
SUBLIMA|Engrandece
LILA|Color morado claro
GNU|Mamífero rumiante, especie de antílope africano
FUNDAMENTO|Razón, motivo
UFANO|Engreído, arrogante
AMAZONA|Mujer guerrera
SERRALLO|Harén - Gineceo
ANTONOMASIA|Figura retórica
UFAR|Robar
RAYAD|Tachad
NIOBE|Hija de Tántalo y esposa de Anfión
El programa podría elegir al azar FUNDAMENTO para la palabra horizontal (ya que tiene al menos 8 letras), y las palabras UFAR, UFANO, SERRALLO, NIOBE y AMAZONA para las verticales. La salida debe ser algo así:

$ python tp2.py -s

CRUCIGRAMA

    1   2   3     4   5

            .         .
        .   .         .
        .   .         .
    .   .   .         .
H   . . . . . . . . . .
    .   .   .     .   .
    .       .     .   .
            .     .
                  .

DEFINICIONES

H. Razón, motivo
1. Robar
2. Engreído, arrogante
3. Harén - Gineceo
4. Hija de Tántalo y esposa de Anfión
5. Mujer guerrera

SOLUCION

    1   2   3     4   5

            S         A
        U   E         M
        F   R         A
    U   A   R         Z
H   F U N D A M E N T O
    A   O   L     I   N
    R       L     O   A
            O     B
                  E
(Si no se hubiese pasado la opción -s no habría salido la sección SOLUCION.)

Parámetros de la línea de comandos
Para leer los parámetros de la línea de comandos, recomendamos utilizar el módulo argparse de la siguiente manera:

import argparse

def main():
    parser = argparse.ArgumentParser(description='Generador de crucigramas')
    parser.add_argument('-s', '--solucion', action='store_true', help='imprimir la solución')
    args = parser.parse_args()

    imprimir_solucion = args.solucion # es True si el usuario incluyó la opción -s

    ...

main()

Material
Archivo CSV con más de 17.500 palabras y definiciones: palabras.zip
