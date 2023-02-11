![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz042text.png)
```.py
from kivymd.app import MDApp
from kivymd.uix.screen import MDScreen


class MysteryPageA(MDScreen):
    pass


class MysteryPageB(MDScreen):
    pass


class quiz042_main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)

    def build(self):
        return


m = quiz042_main()
m.run()

```
```.kv
ScreenManager:
    MysteryPageA:
        name:"MysteryPageA"
    MysteryPageB:
        name:"MysteryPageB"

<MysteryPageA>:
    MDCard:
        md_bg_color:"#AADD99"
        size_hint:.7,.7
        pos_hint:{"center_x":.5,"center_y":.5}
        radius:30,0,0,30 #topleft,topright,bottomleft,bottomright
        orientation:"vertical"
        MDLabel:
            text:"This is mystery page A you pressed the button"
            font_style:"H3"
            size_hint:1,.1
            halign:"center"
            valign:"center"
        MDBoxLayout:
            MDLabel:
                size_hint:.2,.1
            MDRaisedButton:
                size_hint:.2,.1
                text:"Go to page B"
                md_bg_color:"#e63946"
                on_press: root.parent.current="MysteryPageB"
            MDLabel:
                size_hint:.2,.1
<MysteryPageB>:
    MDCard:
        md_bg_color:"#AADD99"
        size_hint:.7,.7
        pos_hint:{"center_x":.5,"center_y":.5}
        radius:30,0,0,30 #topleft,topright,bottomleft,bottomright
        orientation:"vertical"
        MDLabel:
            text:"This is mystery page B you pressed the button"
            font_style:"H3"
            size_hint:1,.01
            halign:"center"
            valign:"center"
        MDBoxLayout:
            MDLabel:
                size_hint:.2,.1
            MDRaisedButton:
                size_hint:.2,.1
                pos_hint_x:"center"
                text:"Go to page A"
                md_bg_color:"#e63946"
                on_press: root.parent.current="MysteryPageA"
            MDLabel:
                size_hint:.2,.1

```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz042test.gif)
