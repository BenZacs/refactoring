# Refactoring
## How-to-survive
From my How-to-survive code : https://github.com/BenZacs/How-to-survive

**build_recx_and_recy() method**
In the `screen.py` file

https://github.com/BenZacs/How-to-survive/blob/master/screen.py

consider this code:
```
def build_recx_and_recy(self):
        recx = []
        recy = []
        for i in self.world.recx_list:
            recx.append(ModelSprite("rectanglex.jpg", model=i))
        for j in self.world.recy_list:
            recy.append(ModelSprite("rectangley.jpg", model=j))
        self.recx = recx
        self.recy = recy
```

* Refactoring Signs: 
  - have many loop in the same function that should be seperate in more method that easier to manage.
  - the name of variable is to confuse

* Refactoring: rename method.
  - `recx` to `rectangles_in_x_axis`
  - `recy` to `rectangles_in_y_axis`
  - `i` and `j` to `rectangle`
```
def build_recx_and_recy(self):
        rectangles_in_x_axis = []
        rectangles_in_y_axis = []
        for rectangle in self.world.rectangles_in_x_axis_list:
            rectangles_in_x_axis.append(ModelSprite("rectanglex.jpg", model=rectangle))
        for rectangle in self.world.rectangles_in_y_axis_list:
            rectangles_in_y_axis.append(ModelSprite("rectangley.jpg", model=rectangle))
        self.rectangles_in_x_axis = rectangles_in_x_axis
        self.rectangles_in_y_axis = rectangles_in_y_axis
```

* Refactoring: Extract method.
```
def build_rectangles_in_x_axis(self):
        rectangles_in_x_axis = []
        for rectangle in self.world.rectangles_in_x_axis_list:
            rectangles_in_x_axis.append(ModelSprite("rectanglex.jpg", model=rectangle))
        self.rectangles_in_x_axis = rectangles_in_x_axis
```

```
def build_rectangles_in_y_axis(self):
        rectangles_in_y_axis = []
        for rectangle in self.world.rectangles_in_y_axis_list:
            rectangles_in_y_axis.append(ModelSprite("rectangley.jpg", model=rectangle))
        self.rectangles_in_y_axis = rectangles_in_y_axis
```
