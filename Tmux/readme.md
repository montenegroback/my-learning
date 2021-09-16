# Taller Tmux

**¿Que es tmux?** - Es un multiplexor de terminales

```bash
  npm run test
```

## Instalación

```bash
  sudo apt-get update && sudo apt install tmux && tmux -V && tmux
```
    

## Prefijo

Los comandos tmux se ejecutan con el prefijo 

**`CTL + b`**


#### Ejemplos

| Prefijo             | Tecla      | Descripción      |
| ----------------- | ------------------------------------------------------------------ | ----------------- |
| **`CTL + b`** | **`T`** | Muestra la Hora |

```bash
  # Para salir de tmux
  exit
```

## Paneles

Definen el area de trabajo, a traves de multiples paneles


#### shortcodes

| Prefijo             | Tecla      | Descripción      |
| ----------------- | ------------------------------------------------------------------ | ----------------- |
| **`CTL + b`** | **`"`** | Crea un panel horizontal |
| **`CTL + b`** | **`%`** | Crea un panel vertical |
| **`CTL + b`** | **`q`** | Muestra los indeces de los paneles |
| **`CTL + b`** | **`(Teclas dirección)`** | Movernos entre paneles |
| **`CTL + b`** | **`o`** | Movernos por medio de los indices |
| **`CTL + b (Dejando presionado)`** | **`(Teclas dirección)`** | Redimencionar panel |
| **`CTL + b`** | **`:`** | Accedemos al promp |

## Ventanas

Definen el área de trabajo, dentro de estas se pueden tener multiples paneles y a su vez multiples ventanas

#### shortcodes

| Prefijo             | Tecla      | Descripción      |
| ----------------- | ------------------------------------------------------------------ | ----------------- |
| **`CTL + b`** | **`c`** | Crea una nueva ventana  |
| **`CTL + b`** | **`indice`** | Moverse entre ventanas |
| **`CTL + b`** | **`n`** | Moverse a la siguiente ventana |
| **`CTL + b`** | **`p`** | Moverse a la anterior ventana |
| **`CTL + b`** | **`f`** | Buscar diferentes ventanas |
| **`CTL + b`** | **`;`** | Renombrar ventana |

## Sesiones

Nos permiten guardar la configuracion de ventanas y paneles

#### shortcodes

| Prefijo             | Tecla      | Descripción      |
| ----------------- | ------------------------------------------------------------------ | ----------------- |
| **`CTL + b`** | **`$`** | Renombrar sesion |
| **`CTL + b`** | **`d`** | Salir sesion (guardando config) |
| **`CTL + b`** | **`( or )`** | Movernos entre sesiones |
| **`CTL + b`** | **`s`** | Listar y moverse entre sesiones |

#### Listar Sesiones

```bash
  tmux ls
```

#### Eliminar sesion

```bash
  tmux kill-session -t <name session>
```

#### Crear sesion

```bash
  tmux new -s <name session>
```

#### Reabrir sesion

```bash
  tmux attach-session -t <name session>
```
