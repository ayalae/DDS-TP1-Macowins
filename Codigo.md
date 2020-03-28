# DDS-TP1-Macowins

## Requerimentos:
-El sistema deberá saber el precio de venta de una prenda, dependiendo su estado.
-El sistema deberá saber el tipo de cada prenda.
-El sistema deberá registrar las ventas.
-El sistema deberá saber las ganancias de un determinado dia.


## Pseudocodigo

class Prenda {
    var property precioBase
    var property tipo
    var property estado
    
    method precio() = self.estado().precio(precioBase)

}

object nuevo {
    method precio(preciobase) = preciobase
}

object promocion {
    var property valorFijo
    method precio(preciobase) = preciobase - valorFijo
}

object liquidacion {
    method precio(preciobase) = preciobase/2
}

class Venta{
    var property prendasVendidas = []
    var property fecha
    
        method cantidadPrendas() = prendasVendidas.size()
        method recargo()
        method precio() = prendasVendidas.sum({prenda => prenda.precio()}) + self.recargo()
}

class VentaEfectivo inherits Venta {
  override method recargo() = 0
}
class VentaTarjeta inherits Venta {
    var property cantCuotas
    var property valorFijo 
  	override method recargo() =cantCuotas * valorFijo + prendasVendidas.sum({prenda => prenda.precio()*0.1})
}
