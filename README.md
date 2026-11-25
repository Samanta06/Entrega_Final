productos = []


def agregar_producto():
    nombre = input("Ingrese el nombre del producto: ").strip()
    categoria = input("Ingrese la categoría del producto: ").strip()

    if not nombre or not categoria:
        print("⚠️ El nombre y la categoría no pueden estar vacíos.\n")
        return

    while True:
        precio_str = input("Ingrese el precio (sin centavos): ").strip()
        try:
            precio = int(precio_str)
            if precio < 0:
                print("⚠️ El precio no puede ser negativo.\n")
                continue
            break
        except ValueError:
            print("⚠️ Ingrese un número entero válido para el precio.\n")

    productos.append([nombre, categoria, precio])
    print(f"✅ Producto '{nombre}' agregado correctamente.\n")


def mostrar_productos():
    if not productos:
        print("\n📭 No hay productos registrados.\n")
        return

    print("\n📦 Lista de productos:")
    for i, p in enumerate(productos, start=1):
        print(f"{i}. Nombre: {p[0]} | Categoría: {p[1]} | Precio: ${p[2]}")
    print()


def buscar_producto():
    if not productos:
        print("\n📭 No hay productos registrados para buscar.\n")
        return

    nombre = input("Ingrese el nombre del producto a buscar: ").strip()
    encontrados = [p for p in productos if p[0].lower() == nombre.lower()]

    if encontrados:
        print("\n🔍 Productos encontrados:")
        for p in encontrados:
            print(f"Nombre: {p[0]} | Categoría: {p[1]} | Precio: ${p[2]}")
        print()
    else:
        print(f"⚠️ No se encontró ningún producto con el nombre '{nombre}'.\n")


def eliminar_producto():
    if not productos:
        print("\n📭 No hay productos para eliminar.\n")
        return

    mostrar_productos()
    try:
        indice = int(input("Ingrese el número del producto a eliminar: ")) - 1
        if 0 <= indice < len(productos):
            eliminado = productos.pop(indice)
            print(f"🗑️ Producto '{eliminado[0]}' eliminado correctamente.\n")
        else:
            print("⚠️ Número inválido.\n")
    except ValueError:
        print("⚠️ Debe ingresar un número válido.\n")


while True:
    print("*******************************")
    print("1 - Agregar producto")
    print("2 - Mostrar lista de productos")
    print("3 - Buscar producto")
    print("4 - Eliminar producto")
    print("5 - Salir")
    print("*******************************")
    opcion = input("Ingrese la opción deseada: ").strip()

    if opcion == "1":
        agregar_producto()
    elif opcion == "2":
        mostrar_productos()
    elif opcion == "3":
        buscar_producto()
    elif opcion == "4":
        eliminar_producto()
    elif opcion == "5":
        print("👋 ¡Hasta luego!")
        break
    else:
        print("⚠️ Opción inválida. Intente nuevamente.\n")
