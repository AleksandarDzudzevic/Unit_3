![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz041text.png)
## Python Code:
```.py
from kivymd.app import MDApp


class quiz041_main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)

    def build(self):
        return

    def change_turn(self, b):
        if self.root.ids.turn_label.text == "It is X's turn":
            self.root.ids.turn_label.text = "It is O's turn"
            b.text_color="black"
            b.text = "X"
            b.font_size = 45
            b.disabled="True"

        else:
            self.root.ids.turn_label.text = "It is X's turn"
            b.font_size=45
            b.text = "O"
            b.text_color="black"
            b.disabled="True"

m = quiz041_main()
m.run()
```
## Kivy Code:
```.kv
Screen:
    size:500,500
    MDBoxLayout:
        id:main_box
        md_bg_color:"#CCFFE5"
        orientation: "vertical"
        size_hint: 1,.95 #percentages do the screen half width and 70% height position
        pos_hint: {"center_x":0.5,"center_y":0.5}
        MDLabel:
            size_hint:1,.1
            text:"TIC TAC TOE by Aleks"
            halign:"center"
            valign:"center"
            font_size:60
        MDLabel:
            size_hint:1,.1
        MDLabel:
            id:turn_label
            size_hint:1,.1
            text:"It is X's turn"
            halign:"center"
            valign:"center"
            font_size:45
            md_bg_color:"#99DDAA"

        MDBoxLayout:
            id:box_one
            orientation:"horizontal"
            pos_hint: {"center_x":0.5,"center_y":0.5}
            size_hint:.6,.25
            md_bg_color:"#CCFFE5"
            MDRaisedButton:
                id:button1
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button2
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button3
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
        MDLabel:
            size_hint:.7,.03
            md_bg_color:"#CCFFE5"

        MDBoxLayout:
            id:box_two
            orientation:"horizontal"
            pos_hint: {"center_x":0.5,"center_y":0.5}
            size_hint:.6,.25
            md_bg_color:"#CCFFE5"
            MDRaisedButton:
                id:button4
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button5
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button6
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                disabled:False
                on_release:
                    app.change_turn(self)
        MDLabel:
            size_hint:1,.03
            md_bg_color:"#CCFFE5"

        MDBoxLayout:
            id:box_three
            orientation:"horizontal"
            pos_hint: {"center_x":0.5,"center_y":0.5}
            size_hint:.6,.25
            md_bg_color:"#CCFFE5"
            MDRaisedButton:
                id:button7
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button8
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
            MDLabel:
                size_hint:.051,1
            MDRaisedButton:
                id:button9
                size_hint:0.3,1
                md_bg_color:"#DDFFBB"
                on_release:
                    app.change_turn(self)
        MDLabel:
            size_hint:1,.03
        MDLabel:
            size_hint:1,.03
```
## Proof:
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz041test.gif)
