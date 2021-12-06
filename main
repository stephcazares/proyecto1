from lifestore_file import lifestore_products as lifestore_products

from lifestore_file import lifestore_sales as lifestore_sales

from lifestore_file import lifestore_searches as lifestore_searches


#ventas: [0 id_sale, 1 id_product,2 score (from 1 to 5), 3 date(01/01/2020 > 012-345-6789), 4 refund (1 for true or 0 to false)] [0,1,2,3]
#busquedas: [0 id_search, 1 id product]
#productos: [0 id_product, 1 name, 2 price, 3 category, 4 stock]

#lifestore_sales = [id_sale, id_product, score (from 1 to 5), date, refund (1 for true or 0 to false)]
#lifestore_products = [id_product, name, price, category, stock]]
#Para obtener las lista de los productos con mayores ventas comienzo por hacer una lista de ventas por producto (ventasxproducto), que me permitira conocer el dato que necesito considerando las devoluciones realizadas...

ventasxproducto = []

for producto in lifestore_products:
  lista = [producto[0], 0]
  ventasxproducto.append(lista)

for venta in lifestore_sales:
  producto_vendido = venta[1]#donde producto_vendido se reviere a la posicion del dato a tomar en cuenta es "product_id"
  no_devuelto = venta[4]#donde no devuelto revisa que todos cumplan el parametro de venta efectiva iterando con "if", siempre que este sea 0 sera incluido.
  if no_devuelto == 0:
    ventasxproducto[producto_vendido - 1][1] += 1 
#print(ventasxproducto)#Compruebo imprimiendo los resultados.

#Aqui ordeno el resultado arrojado por la lista recien creada y en base a ello ordeno los resultados de mayor a menor, para poder seleccionar los productos con más ventas.

ventasxproducto.sort(reverse=True, key=lambda cantventas: cantventas[1])

#Usando la funcion sort, que sirve para ordenar los datos de mi lista, tomando como referencia de mayor a menor con "reverse=True" e indicando que se ordenen de acuerdo al numero de ventas, que en este caso esta en la posicion 1 de la lista.
#print(ventasxproducto[0:5]) #Compruebo imprimiendo los datos que me interesan para completar la asignación "Top 5: Productos más vendidos"

ventasxproducto.sort(key=lambda cantventas: cantventas[1])
#a la lista "ventasxproducto", y la ordeno con la funcion "sort" e indico que se ordene basandose al menor numero de ventas, el cual es obtenido gracias al indice 1 indicado.
#print(ventasxproducto[0:5])#Se comprueba imprimiendo los datos que que deseamos y asi se completa la asignacion "Top 5: Productos menos vendidos"

#Para obtener el total monetario de ventas por mes, primero creo una lista con los nombres de los meses (nombremes), para que estos aparezcan en conjunto con el resultado
nombremes= ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre']
#ventas: 0 id_sale, 1 id_product,2 score (from 1 to 5), 3 date(01/01/2020 > 012-345-6789), 4 refund (1 for true or 0 to false)]
ventasxmes = []#Prosigo a crear una lista para las ventas mensuales (ventasxmes)


for meses in nombremes:
  mes= [meses, 0]
  ventasxmes.append(mes)
#Bucle creado para poner el nombre del mes antes que la cantidad mensual monetaria vendida

for venta in lifestore_sales:
  mesvta = int(venta[3][3:5]) 
  producto = venta[1] 
  precio = lifestore_products[producto - 1][2]
  nodevoluciones= venta[4]
  if nodevoluciones==0:
    ventasxmes[mesvta - 1][1] += precio
#Se crea un bucle para la lista en el que:
# Se convierte a entero al mes de la venta en mesvta, para poder filtrar por mes, buscamos el Numero de producto y el precio y filtramos las ventas reales con la iteracion if y asi, sumar cada venta segun los filtros.
#print(ventasxmes)#Compruebo la informacion obtenida
#Con esto cumplo la asignación "Ingresos mensuales 2020"


#Como la lista de "ventasxproducto" ya esta filtrada y tiene las ventas reales (sin devoluciones), se crea una lista y se considera el valor que se encuentra en la posicion "1" (que es la suma de venta por producto), para sumarse en esta nueva lista, para luego dividirlo entre 12 y asi sacar la cantidad de ventas promedio. 
totalventas=0
for venta in ventasxproducto:
  ventas= venta[1]
  totalventas+= ventas

cantidadventaspromedio=totalventas/12
#print(cantidadventaspromedio)#Se comprueba y se obtiene "Promedio mensual de ventas"


#Al igual que en el promedio de la cantidad de ventas, se realiza una lista para conocer el ingreso promedio mensual, y se busca en la lista "ventasxmes" con la posición "1" para poder realizar la suma en la lista creada y dividirlo entre doce. Adicionalmente se coloca la funcion "int", para obtener un numero entero.

totalingresoventas=0
for venta in ventasxmes:
  ingreso=venta[1]
  totalingresoventas+=ingreso

promediomensualingresos= int(totalingresoventas/12)
#print(promediomensualingresos)#Se comprueba y se completa la asignacion "Promedio mensual de ingresos"

mesesconmasventas= ventasxmes
mesesconmasventas.sort(reverse=True, key=lambda ventasi: ventasi[1])
#print(mesesconmasventas[0:5])


#ventas: [0 id_sale, 1 id_product,2 score (from 1 to 5), 3 date(01/01/2020 > 012-345-6789), 4 refund (1 for true or 0 to false)] [0,1,2,3]
ventas2020= 0#Se crea una una lista que representara el total monetario en ventas
for venta in ventasxproducto:
  producto= venta[0]
  ventas= venta[1]
  precio= lifestore_products[producto-1][2]
  ventas2020 += (ventas*precio)
#En este bucle buscamos el "Id_sale" para luego saber cual el su precio, enseguida con la vairable "ventas" en el que buscamos las ventas realizadas, con esto se van a sumar todas las multiplicaciones de "ventas*precio"
#print(ventas2020)#Se cumple la asignación "Venta total 2020"


#Para poder realizar las listas por top de reseñas, es necesario obtener los valores del total de reseñas por producto, por lo que se crea una lista con todos los productos, que va a contener la suma de las reseñas y la cantidad de las reseñas, esto ultimo para poder sacar un promedio de calificacion por producto y realizar el top.
reseñasxproducto = []
for producto in lifestore_products:
  reseñas = [producto[0], 0, 0]
  reseñasxproducto.append(reseñas)
for totalreseñas in lifestore_sales: 
  numproducto = totalreseñas[1]
  reseñasxproducto[numproducto - 1][2] += 1
for calificaciones in lifestore_sales:
  numproducto = calificaciones[1]
  califproducto = calificaciones[2] 
  reseñasxproducto[numproducto - 1][1] += califproducto

#Ya que tenemos la lista "reseñasxproducto", se crea otra lista en la que se obtendra el promedio de las reseñas brindadas de las ventas.
totalreseñas = []
for producto in reseñasxproducto:
  sumatotalreseñas = producto[1]
  cantidadreseñas = producto[2]
  if cantidadreseñas > 0:#se usa esta sentencia para filtrar los productos que no tienen ventas (o en caso de que existiera una venta sin reseña), pues la lista"reseñasxproducto" contiene los productos que no tuvieron ventas.
    promedio = sumatotalreseñas / cantidadreseñas
    reseñas = [promedio, producto[0], cantidadreseñas]
  totalreseñas.append(reseñas)

totalreseñas.sort(reverse=True, key=lambda reseña: reseña[0])
#print(totalreseñas[0:5])
#print(totalreseñas[-5:-1])#Se ordenan los datos de mayor a menor, considerando como punto el mayor promedio de reseñas obtenido. Con esto se cumple la asignacion de "Top 5: Productos con mejor reseña" y "Top 5 productos con peor reseña."


#Para poder saber cuan
busquedaxproducto = []
for producto in lifestore_products:
  Numproducto = producto[0]
  nombreproducto= producto[1]
  catproducto = producto[3]
  totalbusquedas = 0
  for busqueda in lifestore_searches:
    busquedaproducto = busqueda[1]

    if Numproducto == busquedaproducto:
     totalbusquedas += 1
  if totalbusquedas > 0:
    busquedaxproducto.append([totalbusquedas, Numproducto, nombreproducto,catproducto])
busquedaxproducto.sort(reverse=True)
#print(busquedaxproducto[0:10])
#print(busquedaxproducto[-6:-1])
#Con esto obtenemos "Top 10 productos con mayores busqueda" y 

#Para poder realizar el login del usuario y que este pueda escoger entre lo que se pide en el proyecto, primro realizo un menu el cual va a ser presentado al usuario despues de loggearse.
menu=("""LIFESTORE. MENU PRINCIPAL.
Selecciona la opcion deseada.
1 - Top 5: Productos más vendidos
2 - Top 10:Productos menos vendidos
3 - Ingresos mensuales 2020
4 - Promedio mensual de ingresos y ventas
5 - Venta anual 2020
6 - Meses con más ventas
7 - Top 5: Productos con mejor reseña
8 - Top 5: Productos con peor reseña
9 - Top 10: Productos con mayores busquedas
10- Top 5: Productos con menores busquedas
11- Salir
""")
#USUARIO-ADMINISTRADOR
#Con un ciclo while, creamos la entrada del usuario pidiendo un usuario y contraseña, solo cree un usuario, asi que si coincide con Usuario1 y contraseña 12345, el ciclo se rompera y pasara al siguiente, de lo contrario el ciclo se repetira hasta que proporcione la informacion de inicio de sesion correcta.
while True:
  iniciar=input ("""LIFESTORE
  Buen día. Por favor presiona ENTER para continuar.""")
  nombre_usuario= input("Nombre de usuario: ")
  contraseña= input("Contraseña: ")
  if nombre_usuario == "1" and  contraseña== "1":
    print(menu)
    break

  else:
    print("Usuario o contraseña incorecta, intentelo de nuevo o pongase en contacto con el administrador")

#Se crea otro ciclo While en el que para cada opcion propuesta en el menu del 1 al 11, permita explorar la informacion requerida, al final de cada sentencia if y elif, se indica que oprima la tecla # para volver al menu principal, esta indicacion es otra sentencia if que va a imprimir el menu principal y asi se seguira mostrando hasta que se elija la opcion de salir, la cual va a dar por terminada la sesión y finalizara el ciclo.     
while True:
  respuesta=input("Opcion:  ")
  if respuesta == "1":
    print("Top 5: Productos más vendidos")
    print("[Id del producto, Total de Ventas]")
    ventasxproducto.sort(reverse=True, key=lambda cantventas: cantventas[1])
    print(ventasxproducto[0:5])
    
    print("""

    Para volver al menu principal presione la tecla #""")

  elif respuesta == "2":
    print("Top 10:Productos menos vendidos ")
    print("[Id del producto, Total de Ventas]")
    ventasxproducto.sort(key=lambda cantventas: cantventas[1])
    print(ventasxproducto[0:10])
    
    print("""

    Para volver al menu principal presione la tecla #""")
    
  elif respuesta == "3":
    print("Ingresos mensuales 2020")
    print("[Mes, Ingreso total]")
    print(ventasxmes)
    
    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "4":
    print("Promedio mensual de ingresos y ventas")
    print("Cantidad de ventas promedio mensuales: ", cantidadventaspromedio)
    print("Ingreso promedio mensual: ", totalingresoventas)

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "5":
    print("Venta anual 2020")
    print("Lifestore tuvo una venta anual de ")
    print(ventas2020)

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "6":
    print("Meses con más ventas")
    print("Los meses con más ventas, las cuales rebasan el promedio de ingresos", totalingresoventas, "son: ")
    print(mesesconmasventas[0:5])

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "7":
    print("Top 5: Productos con mejor reseña")
    print("[Promedio total de reseñas, Id del producto, Total de reseñas]")
    totalreseñas.sort(reverse=True, key=lambda reseña: reseña[0])
    print(totalreseñas[0:5])

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "8":
    print("Top 5: Productos con peor reseña")
    print("[Promedio total de reseñas, Id del producto, Total de reseñas]")
    totalreseñas.sort(reverse=True, key=lambda reseña: reseña[0])
    print(totalreseñas[-6:-1])

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "9":
    print("Top 10: Productos con mayores busquedas")
    print("[Busquedas totales, Id del Producto, Nombre del Producto,Categoria del producto]")
    busquedaxproducto.sort(reverse=True)
    print(busquedaxproducto[0:10])

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "10":
    print("Top 5: Productos con mayores busquedas")
    print("[Busquedas totales, Id del Producto, Nombre del Producto,Categoria del producto]")
    busquedaxproducto.sort(reverse=True)
    print(busquedaxproducto[-5:-1])

    print("""

    Para volver al menu principal presione la tecla #""")
  elif respuesta == "#":
    print(menu)
  elif respuesta == "11":
    print("¡Hasta Luego!")
    print("                        LIFESTORE")
    break
  
  else:
    print("Ingrese una opcion valida")
    print(menu)
#elif respuesta == "": print("") print() print() print(""" Para volver al menu principal presione la tecla #: """)
