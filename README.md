# Atonomo2_Simulador_de_tarifas_moviles
Este programa calculará cuánto debe pagar un usuario según su consumo de gigas, aplicando lógica de condicionales (si se pasa del límite) y bucles (menú interactivo).

# DIAGRAMA DE FLUJO Y LA EXPLICACION DE CADA UNO DE LAS VARIABLES 
<img width="1292" height="914" alt="image" src="https://github.com/user-attachments/assets/c7ebea38-24bd-4143-9c54-2b90473cb459" />

# CODIGO DEL PROGRAMA

"""
PROYECTO: Sistema de Facturación de Telecomunicaciones
DESCRIPCIÓN: Este programa calcula el total a pagar de un usuario
basado en su plan y consumo de datos.
AUTOR: [DAVID GANCHALA]
"""

import os

def limpiar_pantalla():
    # Función simple para limpiar la consola (funciona en Windows y Mac/Linux)
    os.system('cls' if os.name == 'nt' else 'clear')

def main():
    continuar = True

    # BUCLE WHILE: Mantiene el programa en ejecución hasta que el usuario decida salir.
    # Cumple con el requisito: "Manejo de estructuras repetitivas".
    while continuar:
        limpiar_pantalla()
        print("="*40)
        print("   SIMULADOR DE PLANES DE TELEFONÍA")
        print("="*40)
        print("1. Plan Básico (5 GB - $20)")
        print("2. Plan Premium (15 GB - $35)")
        print("3. Salir")
        
        opcion = input("\nSeleccione una opción: ")

        if opcion == "1":
            print("\n--- Plan Básico Seleccionado ---")
            # Manejo de errores (Try/Except) para evitar que el programa falle si escriben letras
            try:
                gigas = float(input("Ingrese los Gigas consumidos: "))
                
                # ESTRUCTURA LÓGICA (IF): Verifica si excedió el límite
                if gigas > 5:
                    extra = (gigas - 5) * 5 # Cobramos $5 por cada GB extra
                    total = 20 + extra
                    print(f"¡Atención! Excediste el límite por {gigas - 5:.2f} GB.")
                else:
                    total = 20
                
                print(f"--> Total a pagar: ${total:.2f}")
            except ValueError:
                print("Error: Por favor ingrese un número válido.")
            input("\nPresione Enter para continuar...")

        elif opcion == "2":
            print("\n--- Plan Premium Seleccionado ---")
            try:
                gigas = float(input("Ingrese los Gigas consumidos: "))
                
                # Lógica similar para el plan de 15 GB
                if gigas > 15:
                    extra = (gigas - 15) * 5
                    total = 35 + extra
                    print(f"¡Atención! Excediste el límite por {gigas - 15:.2f} GB.")
                else:
                    total = 35
                
                print(f"--> Total a pagar: ${total:.2f}")
            except ValueError:
                print("Error: Por favor ingrese un número válido.")
            input("\nPresione Enter para continuar...")

        elif opcion == "3":
            print("\nCerrando sistema... ¡Hasta luego!")
            continuar = False # Rompe el ciclo While
            
        else:
            print("\nOpción no válida.")
            input("Presione Enter para intentar de nuevo...")

if __name__ == "__main__":
    main()
