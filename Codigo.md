# DDS-TP1-Macowins

## Requerimentos:
- El sistema deberá saber el precio de venta de una prenda, dependiendo su estado.
- El sistema deberá saber el tipo de cada prenda.
- El sistema deberá registrar las ventas.
- El sistema deberá saber las ganancias de un determinado dia.


## Pseudocodigo:

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
    
   ## Aclaraciones
  - Durante la resolucion del ejercicio descarté que los objetos nuevo, promocion y liquidacion sean clases que hereden de Prenda. Ya que si en algun momento un objeto Prenda tiene que cambiar de estado, siendo clases con herencia, deberia eliminar el objeto existente para crear otro. Mientras que si trato a los estados como atributos de Prenda, al tener que cambiar de estado al objeto en cuestion, el objeto conservará su identidad. 
  - Descarté declarar los "Tipos" de prenda como objetos y los traté como strings, ya que no influye en nada el tipo de prenda(por ahora). Aunque me quedó la duda de si es correcto lo que hice (Me olvidé de escribir la duda en el formulario).
  
   
