![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz040text.png)
```.py
from kivymd.app import MDApp


class quiz40main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)

    def build(self):
        return

    def change_mode(self):
        self.root.ids.main_box.md_bg_color = "black"
        self.root.ids.label.color = "white"
        self.root.ids.button_change.color = "white"


m = quiz40main()
m.run()

```
```.kv
Screen:
    size:500,500
    MDBoxLayout:
        id:main_box
        md_bg_color:"white"
        orientation: "vertical"
        size_hint: 1,.95 #percentages do the screen half width and 70% height position
        pos_hint: {"center_x":0.5,"center_y":0.5}

        MDLabel:
            id:label
            text:"Your Name"
            valign:"center"
            halign:"center"
            color:"black"
            font_size:40
            size_hint:1,.3
        MDRaisedButton:
            id:button_change
            text:"Dark Mode"
            size_hint: 0.3,0.1
            pos_hint_x:0.1
            color:"121212"
            on_release:
                app.change_mode()
      
```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz040test1.png)
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz040test2.png)
## HL Python code
```.py
from kivymd.app import MDApp


class quiz40main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)

    def build(self):
        return

    def change_mode(self):
        self.root.ids.main_box.md_bg_color = "black"
        self.root.ids.label.color = "white"
        self.root.ids.button_change.md_bg_color = "white"
        self.root.ids.button_change.color = "black"


m = quiz40main()
m.run()
```
## HL Kivy code
```.kv
Screen:
    size:500,500
    MDBoxLayout:
        id:main_box
        md_bg_color:"white"
        orientation: "vertical"
        size_hint: 1,.95 #percentages do the screen half width and 70% height position
        pos_hint: {"center_x":0.5,"center_y":0.5}

        MDLabel:
            id:label
            text:"Your Name"
            valign:"center"
            halign:"center"
            color:"black"
            font_size:40
            size_hint:1,.3
        MDRaisedButton:
            id:button_change
            size_hint: 0.3,0.1
            pos_hint_x:0.5
            md_bg_color:"black"
            on_release:
                app.change_mode()
            MDLabel:
                id:button_change
                text:"Change mode"
                color:"white"
                halign:"center"

```
