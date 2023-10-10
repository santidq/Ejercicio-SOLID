# OPEN/CLOSE PRINCIPLE (Principio de Abierto/Cerrado)

Los objetos o entidades deben estar abiertos para la extensión, pero cerrados para la modificación.


> Intentar llevar a cabo este principio al 100% es básicamente imposible, ya que es muy complicado prever todos los posibles casos que pueda tener, por lo que es aconsejable solo aplicarlas cuando realmente sea necesario, ya que muchas veces puede llegar a complicar el código, tan así, que se puede volver muy difícil de mantener.

# Ejercicio:

* Aplicar el principio de abierto/cerrado en el siguiente ejemplo de código:

```ts
interface Descuento {
    aplicarDescuento(precio: number): number;
}

class DescuentoPorcentaje implements Descuento {
    constructor(private porcentaje: number) {}

    aplicarDescuento(precio: number): number {
        const descuento = (this.porcentaje / 100) * precio;
        return precio - descuento;
    }
}

class DescuentoFijo implements Descuento {
    constructor(private cantidad: number) {}

    aplicarDescuento(precio: number): number {
        return precio - this.cantidad;
    }
}

class Producto {
    constructor(
        private nombre: string,
        private precio: number
    ) {}

    getNombre(): string {
        return this nombre;
    }

    getPrecio(): number {
        return this.precio;
    }

    aplicarDescuento(descuento: Descuento): number {
        return descuento.aplicarDescuento(this.precio);
    }
}

// Ejemplo de uso:
const producto = new Producto("Producto de ejemplo", 100);
const descuentoPorcentaje = new DescuentoPorcentaje(10);
const descuentoFijo = new DescuentoFijo(20);

const precioConDescuentoPorcentaje = producto.aplicarDescuento(descuentoPorcentaje);
const precioConDescuentoFijo = producto.aplicarDescuento(descuentoFijo);

console.log("Precio con descuento porcentaje:", precioConDescuentoPorcentaje);
console.log("Precio con descuento fijo:", precioConDescuentoFijo);

```

* Su tarea radica en lograr que el siguiente código este abierto para la extensión, pero cerrado para la modificación. En otras palabras, que se pueda agregar un nuevo tipo de descuento sin tener que modificar la clase `Producto`.
