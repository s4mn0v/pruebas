```mermaid
erDiagram
    CLIENTE {
        int numero_cliente PK "Número de cliente (único)"
        string direcciones_envio "Direcciones de envío (varias)"
        float saldo "Saldo"
        float limite_credito "Límite de crédito (máx $3.000.000)"
        float descuento "Descuento"
    }

    ARTICULO {
        int numero_articulo PK "Número de artículo (único)"
        string fabricas "Fábricas que lo distribuyen"
        int existencias "Existencias en cada fábrica"
        string descripcion "Descripción del artículo"
    }

    PEDIDO {
        int numero_cliente FK "Número de cliente"
        string direccion_envio "Dirección de envío"
        datetime fecha_pedido "Fecha del pedido"
    }

    LINEA_PEDIDO {
        int numero_pedido FK "Número de pedido"
        int numero_articulo FK "Número del artículo pedido"
        int cantidad "Cantidad"
    }

    FABRICA {
        int numero_fabrica PK "Número de fábrica (único)"
        string telefono_contacto "Teléfono de contacto"
        int total_articulos "Total de artículos proveídos"
    }

    CLIENTE ||--o{ PEDIDO : realiza
    PEDIDO ||--o{ LINEA_PEDIDO : contiene
    LINEA_PEDIDO }o--|| ARTICULO : incluye
    ARTICULO ||--o{ FABRICA : distribuido_por
```

```mermaid
erDiagram
    CLIENTES {
        int NumeroCliente PK
        string DireccionesEnvio
        float Saldo
        float LimiteCredito
        float Descuento
    }
    
    ARTICULOS {
        int NumeroArticulo PK
        string Descripcion
    }
    
    FACTORIAS {
        int NumeroFabrica PK
        string TelefonoContacto
    }
    
    PEDIDOS {
        int NumeroCliente FK
        string DireccionEnvio
        datetime FechaPedido
        string NumeroArticulo FK
        int Cantidad
    }

    CLIENTES ||--o{ PEDIDOS: "realiza"
    ARTICULOS ||--o{ PEDIDOS: "incluye"
    FACTORIAS ||--o{ ARTICULOS: "distribuye"

    PEDIDOS {
        int LineaPedido PK
        int NumeroCliente FK
        string DireccionEnvio
        datetime FechaPedido
        int NumeroArticulo FK
        int Cantidad
    }

    FACTORIAS ||--o{ ARTICULOS: "distribuye"
```



```
npm i
```

```
npm run dev
```
