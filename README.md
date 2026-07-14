
recorridos = { 
    'R001': ['Santiago', 'Valparaíso', 120, 'normal', 'día', True],
    'R002': ['Santiago', 'Concepción', 500, 'cama', 'noche', True],
    'R003': ['La Serena', 'Coquimbo', 15, 'normal', 'día', False],
    'R004': ['Temuco', 'Valdivia', 165, 'semi-cama', 'día', True],
    'R005': ['Iquique', 'Arica', 310, 'cama', 'noche', False],
    'R006': ['Santiago', 'Rancagua', 90, 'normal', 'día', True],
}


ventas = {

    'R001': [7990, 20],
    'R002': [25990, 0],
    'R003': [1990, 35],
    'R004': [12990, 8], 
    'R005': [18990, 3],
    'R006': [4990, 12],

}

def validar_origen():
    while True:
      origen = input("Ingrese ciudad de origen")
      if origen != "":
            return origen
            print("No se puede dejar espacios en blanco")

def validar_Destino():
    while True:
      destino = input("Ingrese ciudad de origen")
    if destino != "":
            return destino
            print("No se puede dejar espacios en blanco")


def distancia_km():
    while True:
        try:
            kilometros = int(input("Cuantos kilometroa tiene su viaje"))
            if kilometros == 0:
                print("Debe ser un numero mayor a cero!")
            elif kilometros < 0:
                print("El numero ingresado no puede ser menor a cero!")
            else:
                return kilometros
        except Exception:
            print("Solo se pueden numeros enteros")

def validar_tipo_bus():
    while True:
        tipo = input("En que tipo de bus viaja?, normal, semi-cama o cama?").lower().strip()
        if tipo == "normal" or tipo == "semi-cama" or tipo == "cama":
            return tipo
        
        print("Tipo De Bus Invalido")


def validar_servicio():
    while True:
        servicio = input("Que servicio tiene?(Diurno/Nocturno)")
        
        if servicio == "diurno" or servicio == "nocturno":
            return servicio
        
        print("Servicio INvalido")


def validar_wifi():
    while True:
        wifi = input("Tine servicio a wifi? (Si / NO)").upper().strip()

        if wifi == "si":
            return True
        elif wifi == "no":
            return False
        print("Escoja solo Si o No")

def precio():
    while True:
        try:
            precio = int(input("Cuanto costo su viaje?"))
            if precio == 0:
                print("Debe ser un numero mayor a cero!")
            elif precio < 0:
                print("El numero ingresado no puede ser menor a cero!")
            else:
                return precio
        except Exception:
            print("Solo se pueden numeros enteros")

def validar_asientos():
    while True:
        try:
            asientos = int(input("Ingrese cantidad de asientos disponibles: "))
            
            if asientos >= 0:
                return asientos
            
            print("La cantidad de asientos debe ser igual o mayor a cero!")
        
        except ValueError:
            print("Solo se pueden ingresar numeros enteros")

def asientos_origen(origen, recorrido, ventas):
    asientos = 0

    for codigo in recorrido:
        if recorrido[codigo][1] == origen:
            asientos += ventas[codigo][1]
        print("La cantidad total de asientos es de: ", asientos)

def actualizar_precio(codigo, nuevo_precio):
    codigo_upper = codigo.strip().upper()
    if codigo_upper in ventas:
        ventas[codigo_upper][0] = nuevo_precio
        return True
    return False



                                 
                             

def menu(menu):
    print("==========Menú===========")
    print("1.- Asientos por ciudad de origen")
    print("2.- Busqueda de recorridos por rango de precio")
    print("3.- Actualizar precio de recorrido")
    print("4.- Agregar REcoirrido")
    print("5.- Eliminar Recorrido")
    print("6.- Salir")
    print("==========================")

opcion =input("ingrese una opcion: ")

if opcion == "1":
  origen = input("Ingrese la ciudad de origen: ")
  asientos_origen(origen)

if opcion == "2":
    while True:
        try:
            p_min = int(input("Ingrese precio minimo: ")).strip()
            p_max = int(input("Ingrese precio maximo: ")).strip()

            if p_min < 0 or p_max < 0:
                print("El precio debe ser mayor o igual a cero!")
                continue
            
            if p_min > p_max:
                print("El precio minimo no puede ser mas grande que el maximo")
                continue
        except ValueError:
            print("Solo se pueden ingresar numeros enteros!")
        
busqueda_precios = (p_min, p_max)

if opcion == 3:
    while True:
        codigo = input("ingrese el codigo del reocrrido que se actualizara: ").strip()
        while True:
            nuevo_precio_str = input("Ingrese el nuevo precio: ").strip()
            try:
                nuevo_precio =int(input(nuevo_precio_str))
                if nuevo_precio > 0:
                    break
                else:
                    print("El precio debe ser un numero mayor a cero")
            except ValueError:
                if actualizar_precio(codigo, nuevo_precio)                    


