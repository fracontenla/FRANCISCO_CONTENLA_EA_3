# FRANCISCO_CONTENLA_EA_3
import os

largoFila = 5
largoColumnas = 10
asientos = [[(( fil * 10) + col + 1) for col in range(largoColumnas)] for fil in range(largoFila)]
precios = [100_000,100_000,50_000,10_000,10_000]

def mostrar():

    print("\n\t")
    for fila in asientos:
        for columna in fila:
            if type(columna) is int or columna is float:
               
                numero_mostrar = f"[ {columna}  ]" if columna < 10 else f"[ {columna} ]"
                
                print(numero_mostrar, end="")
            else:
                print("( X  )", end="")
        print("\t")

def comprar(rut):

    mostrar()
    try:
        compra = int(input("\n\tingrese asiento a comprar >> "))
    except(ValueError, TypeError):
        print(f"\n\n\tINGRESE OPCION VALIDA ENTRE 1 Y {largoFila * largoColumnas} compra no efectuada")
        compra = 0
        return False

    if compra in range(1, (largoFila*largoColumnas)):

        if (compra % 10) != 0:
            fila = compra//largoColumnas
            columna = (compra % largoColumnas) -1
        else:
            fila = (compra//largoColumnas) -1
            columna = largoColumnas -1
        if type(asientos[fila][columna]) is int or type(asientos[fila][columna]) is float:
            asientos[fila][columna] = rut
            print("\n\tAsiento comprado\n")
            return True
        
        else:
            print("\n\tAsiento Ocupado, Compra NO Efectuada\n")
            return False
    else:
        print(f"\n\tAsiento no Valido ingrese opcion entre 1 y {largoFila * largoColumnas} , Compra NO Efectuada\n")
        return False

def ganancias_totales():
    ganancia = 0
    contador = 0
    fila = 0
    
    while fila < len(asientos):
        columna = 0
        
        while columna < len(asientos[fila]):

            if type(asientos[fila][columna]) is str: 
                ganancia += precios[fila]
                contador+=1
            
            columna += 1

        fila += 1

    print(f"\n\n\tSe han vendido {contador} entradas con una ganancia total de { " {:,}".format(ganancia).replace(",",".") }\n\n")

def compradores():
    fila = 0
    
    while fila < len(asientos):
        columna = 0
        
        while columna < len(asientos[fila]):
            
            if type(asientos[fila][columna]) is str: 
                
                
                asiento = (fila * largoColumnas ) + columna + 1
                print(f"\tCliente : {asientos[fila][columna]} asiento: {asiento} valor entrada: ${ "{:,}".format(precios[fila]).replace(",",".") }")
            
            columna += 1

        fila += 1

while True:
    os.system('cls')

    print("\n\n\t MENU PRINCIPAL ")
    print("\n\tOpcion 1: Comprar entradas")
    print("\tOpcion 2: Mostrar ubicaciones")
    print("\tOpcion 3: Mostrar ganancias totales")
    print("\tOpcion 4: Mostrar asistentes")
    print("\tOpcion 5: Salir")
           
    opcion = int(input("\t>> <<\b\b\b"))

    if opcion == 5:
        print ("francisco contenla, 26/06/2024")
        break
    elif opcion == 1:
        os.system("cls")

        print("\n\n\t MENU COMPRA ENTRADAS ")

        rut = input("\n\tIngrese Rut compra  ")
        opcionCompra = -1
        while opcionCompra not in (0,1,2):
            opcionCompra = int(input("\tCuantas entradas quiere comprar? 0,1,2 > "))
            
            if opcionCompra not in (0,1,2):
                print("\n\n\t ingrese una de las opciones  0, 1, 2\n\n")


        if opcionCompra != 0:
            contador = 0 
            while contador < opcionCompra:
                compra_hecha = comprar(rut)
                if compra_hecha:
                    contador += 1
                
        input("\n\n\tpresione ENTER para continuar ")
    elif opcion == 2:
        os.system("cls")

        print("\n\n\t MOSTRAR UBICACIONES ")
        mostrar()
        
        input("\n\n\t presione ENTER para continuar ")

    elif opcion == 3:
        os.system("cls")

        print("\n\n\t GANANCIAS TOTALES")
        ganancias_totales()

        input("\n\n\t presione ENTER para continuar ")

    elif opcion == 4:
        os.system("cls")

        print("\n\n\t LISTA DE ASISTENTES ")
        compradores()

        input("\n\n\t presione ENTER para continuar ")
    else:
        print("opcion invalida")
        input("\n\n\t presione ENTER para continuar ")
