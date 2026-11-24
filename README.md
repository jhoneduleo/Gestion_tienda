class Producto:
    def __init__(self, nombre, precio, stock):
        self.nombre = nombre
        self.precio = precio
        self.stock = stock

    def reducir_stock(self, cantidad):
        if self.stock >= cantidad:
            self.stock -= cantidad
            return True
        return False


class Tienda:
    def __init__(self, nombre):
        self.nombre = nombre
        self.caja = 0.0

    def vender(self, producto, cantidad):
        # Interacción: El objeto Tienda modifica el estado del objeto Producto
        if producto.reducir_stock(cantidad):
            total = producto.precio * cantidad
            self.caja += total
            print(f"Venta exitosa: {cantidad}x {producto.nombre} | Total: ${total}")
        else:
            print(f"Stock insuficiente de {producto.nombre}")


# --- DEMO DE FUNCIONAMIENTO (Instanciación e interacción) ---
# 1. Instanciación de objetos de dos clases distintas
mi_tienda = Tienda("TechStore")
laptop = Producto("Laptop", 1000, 5)

# 2. Interacción entre ambos objetos
print(f"Stock inicial de {laptop.nombre}: {laptop.stock}")
mi_tienda.vender(laptop, 2)
print(f"Stock restante: {laptop.stock} | Dinero en caja: ${mi_tienda.caja}")
