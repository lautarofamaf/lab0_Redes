
# Punto Estrella: Nombres de Dominio con Caracteres Especiales

Los nombres de dominio como `http://中文.tw/` y `https://💩.la1/` funcionan gracias al sistema **IDN (Internationalized Domain Names)**, que permite usar caracteres Unicode en la web. 

## Funciona de la siguiente manera
El protocolo DNS solo admite caracteres ASCII, por lo que los nombres de dominio con caracteres especiales se convierten a **Punycode**.

Ejemplos de conversión:
- `中文.tw` → `xn--fiq228c.tw`
- `💩.la1` → `xn--ls8h.la1`

El prefijo `xn--` indica que el dominio ha sido convertido a Punycode

## Conversión en Python
Podemos usar la biblioteca `idna` para convertir nombres de dominio:

```python
import idna

print(idna.encode("中文.tw").decode())  # xn--fiq228c.tw
print(idna.decode("xn--fiq228c.tw"))  # 中文.tw
```
