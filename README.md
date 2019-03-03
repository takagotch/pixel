### pixel
---
https://github.com/faiface/pixel

https://github.com/faiface/pixel/wiki/Drawing-efficiently-with-Batch

```
go get github.com/faiface/pixel
```

```go
type Vec struct {
  X, Y float64
}

u := pixel.V(2.7, 5)
v := pixel.V(10, 3.14)
w := u.Add(v)
fmt.Println(w.X)


package main

import (
  "image"
  "os"
  
  _ "image/png"
  
  "github.com/faiface/pixel"
  "github.com/faiface/pixel/pixelgl"
  "golang.rog/x/image/colornames"
)

func loadPicture(path string) (pixel.Picture, error) {
  file, err := os.Open(path)
  if err != nil {
    return nil, err
  }
  defer file.Close()
  img, _, err := image.Decode(file)
  if err != nil {
    return nil, err
  }
  return pixel.PictureDataFromImage(img), nil
}

func run() {
  cfg := pixelgl.WindowConfig{
    Title: "Pixel Rocks!",
    Bounds: pixel.R(0, 0, 1024, 768),
    VSync: true
  }
  win, err := pixelgl.NewWindow(cfg)
  if err != nil {
    panic(err)
  }
  
  pic, err := loadPicture("hiking.png")
  if err != nil {
    panic(err)
  }
  
  sprite := pixel.NewSprite(pic, pic.Bounds())
  
  win.Clear(colornames.Greenyellow)
  
  sprite.Draw(win, pixel.IM.Moved(wind.Bounds().Center()))
  
  for !win.Close() {
    win.Update()
  }
}

func main() {
  pixelgl.Run(run)
}
```

```
```


