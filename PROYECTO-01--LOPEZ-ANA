# PROYECTO-01--LOPEZ-ANA.
Este es un código que permite obtener listas de datos clasificadas para poder ver y tener un panorama de las ventas  y búsquedas de la tienda del caso práctico LifeStore

#NOMBRE DE USUARIO, CONTRASEÑA
lista_admins = [["Admin", "8888"], ["Assitant", "0000"]]

usuario = input("Enter Username: ")
password = input("Enter password: ")

is_admin = 0 #SI ES 1, ES ADMIN. SI ES 0 , NO ES ADMIN
trys = 0

while is_admin != 1 and trys < 3:
	for admin in lista_admins:
		if admin[0] == usuario and admin[1]==password:
			is_admin = 1
if is_admin == 0:
      print("Incorrect data")
      usuario = input("Input username again: ")
      password = input("Input password again: ")
      trys += 1
if is_admin == 1:
	print("Welcome to sales record system")

from lifestore_file import lifestore_searches
from lifestore_file import lifestore_sales 
from lifestore_file import lifestore_products
#####################################################

'''RESOLVÍ PODER SACAR DATOS MENSUALES, SIN EMABRGO, DEBIDO A LA CANTIDAD DE INFO. CONSIDERO QUE ES MEJOR UN ANÁLISIS ANUAL, ME PERMITIÓ OBSERVAR EL # DE VENTAS Y MESES CON MAYOR VENTAS

mes = input(str("Write the number of the month(format:00) you want to find out sale records: \n01: Enero\n02: Febrero\n03: Marzo\n04: Abril\n05: Mayo\n06: Junio\n07: Julio\n08: Agosto\n09: Septiembre\n10: Octubre\n11: Noviembre\n12: Diciembre\n>>:  "))
trys = 0

list_m_sales = []
for fecha in lifestore_sales:
  if fecha[3][3:5] == mes and fecha[4] == 1:
    sale = ([fecha[1],fecha[4],fecha[3]])
    list_m_sales.append(sale)
    print(list_m_sales)
    fecha = 0'''
###################################################
#INICIO DEL CÓDIGO CON UN WHILE CONDICIONADO POR IFS Y UN ÍNDICE PARA PODER NAVEGAR ENTRE LAS FUNCIONES

ans = True
while ans:
    print ('''
    1.Top 50 sales And List product/categories less sales
    2.Most searched prodcuts and Less searched products
    3. Products with Best reviews and Worst Reviews 
    4. Exist''')
    ans=input("What would you like to do?" )
    
    if ans == "1": 
    
      #SE GENERA UNA NUEVA LISTA SIMPLIFICADA, CON LOS VALORES QUE SE UTILIZARÁN EN EL RESTO DEL CÓDIGO PARA VENTAS Y PRODUCTOS
      list_sales = []
      n = 0
      for sale in lifestore_sales:
        sale = [[lifestore_sales[n][1]],[lifestore_sales[n][4]],[lifestore_sales[n][2]]] 
        list_sales.append(sale) #ID,VENTA/REFUND
        n += 1

      list_products = []
      n = 0
      for product in lifestore_products:
        product = [[lifestore_products[n][0]],[lifestore_products[n][3]],[lifestore_products[n][1]]] #ID,CATEGORÍA,NOMBRE 
        list_products.append(product)
        n += 1
      
      #SE CONCATENA Y SUMA EL NUMERO DE VENTAS POR PRODUCTO
      svr = 0 #SALES VS REFUND
      for prod in list_products:
        for sold in list_sales:
          if prod[0] == sold[0]:
            if sold[1] == [0]:
              svr += 1
            else:
              svr -= 1
        prod.append(svr)  #ID,CATEGORIA,NOMBRE, #VENTAS
        svr = 0
        
      #SE DEFINE UNA FUNCIÓN QUE PERMITE CALCULAR EL NÚMERO MÁXIMO DE UNA LISTA CONSIDERANDO LA POSICIÓN DE LA LISTA, QUE SE VA A REORDENAR
      def max_lists(data, num, positon): #DATA= LISTA, NUME = RANGO (TOP50), POSITION = POSICIÓN DE LA LISTA[]
          results = sorted(data, key=lambda x: max(x[positon:]), reverse=True)
          return results[:num]

      #CÁLCULO DEL TOP 50 CON FUNCIÓN
      top_50 = max_lists(list_products, 50, 3)

      
      #IMPRIMIR EL TOP 50, SOLO CATEGORÍA, NOMBRE Y TOTAL DE  VENTAS
      sale_names = []
      m = 0  
      for name in top_50:
        name = [top_50[m][1],top_50[m][2],top_50[m][3]]
        sale_names.append(name)
        m += 1
        
      #RESULTADO DEL IF  
      print("The top 50 product sold where:")
      print(sale_names)
        
      '''Por categoría, generar un listado con los 50 productos con menores ventas '''


      #SE DEFINE UNA FUNCIÓN QUE PERMITE CALCULAR EL NÚMERO MÍNIMO DE UNA LISTA CONSIDERANDO LA POSICIÓN DE LA LISTA, QUE SE VA A REORDENAR DEL MAYOR AL MENOR

      def min_lists(data, num, positon): #DATA= LISTA, NUME = RANGO (TOP50), POSITION = POSICIÓN DE LA LISTA[]
          results = sorted(data, key=lambda x: min(x[positon:]))
          return results[:num]

      less_50 = min_lists(list_products, 50, 3)

      #PARA IMPRIMIR EL TOP 50, SOLO CATEGORÍA, NOMBRE Y TOTAL DE  VENTAS
      sale_names = []
      m = 0  
      for name in less_50:
        name = [less_50[m][1],less_50[m][2],less_50[m][3]]
        sale_names.append(name)
        m += 1
      
      #RESULTADO DEL IF
      print("#\n\n\n\n\nThe products with the lowest sales where:")  
      print(sale_names)
      
          elif ans == "2":
      def min_lists(data, num, positon): #DATA= LISTA, NUME = RANGO (TOP50), POSITION = POSICIÓN DE LA LISTA[]
          results = sorted(data, key=lambda x: min(x[positon:]))
          return results[:num]
      def max_lists(data, num, positon): #DATA= LISTA, NUME = RANGO (TOP50), POSITION = POSICIÓN DE LA LISTA[]
          results = sorted(data, key=lambda x: max(x[positon:]), reverse=True)
          return results[:num]

          '''Uno los 100 productos con mayor búsquedas'''
          
       #CREAMOS UNA NUEVA LISTA SOLO CON LOS VALORES DE ID
      list_searches = []
      n = 0
      for search in lifestore_searches:
          list_searches.append(search[1])
          n += 1
          
        #DEFINIMOS UNA FUNCION QUE CUENTA LAS VECES QUE EL ID DEL PRODCUTO SE REPITE, CONSIDERANDO QUE ES UNA LISTA SIMPLE Y POSTERIRMENTE SE CREA UNA NUEVA LISTA QUE ANIDA Y          RELACIONA LOS VALORES ENTRE ID Y CANTIDAD DE VECES REPETIDA
      def most_rep(lista):
        num = []
        for i in lista:
          curr_freq = lista.count(i)
          if not i in (f for sublist in num for f in sublist):
            num.append([i,curr_freq])
        return num
        
        #UTILIZAMOS LA FUNCION CREADA ANTERIORMENTE PARA ENCONTRAR MÁXIMOS, Y AHORA RELACIONADA CON LA FUNCIÓN QUE NOS DA EL # DE VECES REPETIDOS POR CODIGO
        top_100 = max_lists(most_rep(list_searches), 100, 1)
        #BUSCAMOS LA RELACION DE LOS ID, CON SU NOMBRE -CATEGORÍA Y LO CONCATENAMOS CON LA LISTA DE PRODCUTOS DEL TOP 100 QUE YA TENÍAMOS
        for prod in top_100:
          for articulo in list_products:
            if prod[0] == articulo[0][0]:
              name = articulo[2],articulo[1]
              prod.append(name)   #ID,#BUSQUEDAS,NOMBRE,CATEGORIA
              
        #RESULTADO DEL IF      
        print("The top products searched \n where: ")
        print(top_100)
        print("They where: ")
        print(len(top_100))
        
        '''Con los 100 productos con menores búsquedas'''
      list_sales = []
      n = 0
      for sale in lifestore_sales:
        sale = [[lifestore_sales[n][1]],[lifestore_sales[n][4]],[lifestore_sales[n][2]]] 
        list_sales.append(sale) #ID,VENTA/REFUND
        n += 1
      list_products = []
      n = 0
      for product in lifestore_products:
        product = [[lifestore_products[n][0]],[lifestore_products[n][3]],[lifestore_products[n][1]]] #ID,CATEGORÍA,NOMBRE 
        list_products.append(product)
        n += 1
      #IMPRIMIR EL TOP_BOTTOM 100, SOLO CON NOMBRE Y TOTAL DE VENTAS
      less_100 = min_lists(most_rep(list_searches), 100, 1)
      #BUSCAMOS LA RELACION DE LOS ID, CON SU NOMBRE Y LO CONCATENAMOS CON LA LISTA DE PRODCUTOS DEL TOP 100 QUE YA TENÍAMOS
      for prod in less_100:
        for articulo in list_products:
          if prod[0] == articulo[0][0]:
            name = articulo[2],articulo[1]
            prod.append(name)   #ID,#BUSQUEDAS,NOMBRE,CATEGORIA
            
        #RESULTADO DEL IF    
        print("The products with less searches\n where: ")
        print(less_100)
        print("They where:\n ")
        print(len(less_100))
        
        
    elif ans == "3":
      def min_lists(data, num, positon): 
          results = sorted(data, key=lambda x: min(x[positon:]))
          return results[:num]
      def max_lists(data, num, positon): 
          results = sorted(data, key=lambda x: max(x[positon:]), reverse=True)
          return results[:num]
      list_sales = []
      n = 0
      for sale in lifestore_sales:
        sale = [[lifestore_sales[n][1]],[lifestore_sales[n][4]],[lifestore_sales[n][2]]] 
        list_sales.append(sale) #ID,VENTA/REFUND
        n += 1
      list_products = []
      n = 0
      for product in lifestore_products:
        product = [[lifestore_products[n][0]],[lifestore_products[n][3]],[lifestore_products[n][1]]] #ID,CATEGORÍA,NOMBRE 
        list_products.append(product)
        n += 1
        
      #ESTA PARTE DEL CODIGO NOS PERMITE CLASIFICAR DEPENDIENDO EL REVIEW Y ELIMINANDO DATOS DUPLICADOS. PARA MÁXIMOS Y MÍNIMOS
      list_top_scores = []
      list_bottom_scores = []
      for prod in list_products:
        element_max = [[prod[0][0]],[prod[2][0]]]
        element_min = [[prod[0][0]],[prod[2][0]]]
        max_value = 0
        min_value = 0
        for review in list_sales:
          if prod[0][0] == review[0][0]: 
            max_value = review[2][0]  
            min_value = review[2][0]
            if review[2][0] > max_value:
              max_value = review[2][0]
            if review[2][0] < min_value:
              min_value = review[2][0]
        element_max.append(max_value)
        element_min.append(min_value)
        list_top_scores.append(element_max)
        list_bottom_scores.append(element_min)
        
        #SE HACE LA LISTA DE LOS TOP 10
        top_10 = max_lists(list_top_scores, 10, 2)  
        
      #BUSCAMOS LA RELACION DE LOS ID, CON SU NOMBRE -CATEGORÍA Y LO CONCATENAMOS CON LA LISTA DE PRODCUTOS DEL TOP 10 QUE YA TENÍAMOS
      for prod in top_10:
        for articulo in list_products:
          if prod[0] == articulo[0][0]:
            name = articulo[2],articulo[1]
            prod.append(name)   #ID,#BUSQUEDAS,NOMBRE,CATEGORIA
       
      #RESULTADO DEL IF  
      print("The top 10 products with best reviews \n where:")
      print(top_10)
      
      '''Otro para las peores, considerando los productos con devolución'''
      list_sales = []
      n = 0
      for sale in lifestore_sales:
        sale = [[lifestore_sales[n][1]],[lifestore_sales[n][4]],[lifestore_sales[n][2]]] 
        list_sales.append(sale) #ID,VENTA/REFUND
        n += 1
      list_products = []
      n = 0
      for product in lifestore_products:
        product = [[lifestore_products[n][0]],[lifestore_products[n][3]],[lifestore_products[n][1]]] #ID,CATEGORÍA,NOMBRE 
        list_products.append(product)
        n += 1

      new_list_bottom_scores = []
      for worst in list_bottom_scores:
        if worst[2] != 0:
          new_list_bottom_scores.append(worst)

      less_10 = min_lists(new_list_bottom_scores, 10, 2)
      
      #RESULTADO DEL IF
      print("The top 10 products with worst reviews \n where:")
      print(less_10)
      
      #SE CIERRA EL MENÚ
    elif ans == "4":
      print("Thank you")
 
  

