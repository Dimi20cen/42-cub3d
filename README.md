
# Cub3D

A small **ray-casting** engine inspired by *Wolfenstein 3D*, built for the 42 curriculum.  
Navigate a maze from a first-person view with textured walls, simple lighting, and smooth movement.

## ✨ Features

- Ray-casting renderer (per-column DDA)
- Textured walls (N/S/E/W)
- Player movement & rotation (smooth, frame-rate independent)
- Collision with map walls
- `.cub` map/config parsing:
  - Texture paths: `NO`, `SO`, `WE`, `EA`
  - Colors: `F` (floor), `C` (ceiling) in `R,G,B`
  - Map grid with `0/1` and player start `N/S/E/W`
- Error handling for invalid configs & open maps
- Clean exit and resource teardown

> Repo layout includes **minilibx**, **libft**, **gnl**, **maps**, and **textures** with a standard **Makefile**.

## 🕹 Controls (default)

- **W / A / S / D** — move forward/left/back/right  
- **← / →** — rotate view  
- **ESC** — quit  
- Window close (❌) — quit

## 🛠 Build & Run

### Requirements
- **gcc/clang**, **make**
- **MiniLibX** (bundled in `minilibx/`)
- X11/GL (Linux) or native frameworks (macOS)

### macOS
```bash
make
./cub3d maps/sample.cub
````

### Linux (Debian/Ubuntu)

You may need X11 dev headers if not present:

```bash
sudo apt-get update
sudo apt-get install build-essential xorg libxext-dev libbsd-dev
make
./cub3d maps/sample.cub
```

## 📂 Project Structure

```
42-cub3d/
├─ driver/           # input loop / frame timing (if used)
├─ gnl/              # get_next_line for file IO
├─ img/              # (optional) images/helpers
├─ libft/            # common C utils
├─ maps/             # .cub configs + map files
├─ minilibx/         # graphics lib (MLX)
├─ src/              # parsing, raycasting, rendering, hooks
├─ textures/         # wall textures
├─ subject/          # 42 subject PDF
├─ Makefile
└─ screen-capture.gif
```


## 🧾 `.cub` File Format (example)

```text
NO textures/north.xpm
SO textures/south.xpm
WE textures/west.xpm
EA textures/east.xpm
F  40,40,40
C  135,206,235

1111111111
1000000001
10N0000001
1000010001
1111111111
```

- Player start is one of **N/S/E/W** inside the map.
- Map must be **enclosed** (no leaks to the outside).
- Exactly one spawn; all required textures/colors present.

## 📖 Learning Outcomes

- Implementing a classic **DDA ray-caster**
- Resource & memory management (textures, images, buffers)
- Real-time input & frame rendering with **MiniLibX**
- Robust file parsing & validation
- Clean error paths and teardown
