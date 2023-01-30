# Example 1
### Python code 
```.py
from kivymd.app import MDApp


class example1(MDApp):
    def build(self):
        return


test = example1()
test.run()

```
### Kivy code
```.kv
Screen:
    size:500,500

    MDLabel:
        text:"Hello world"
        halign:"center"
        font_size:"35pt
```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/gui_task_eg1pic.png)
# Example 2
### Python code 
```.py
```
### Kivy code
```.kv
```
![]()
# Example 3
### Python code 
```.py
```
### Kivy code
```.kv
```
![]()


# TASK 1

### Python code
```.py
from kivymd.app import MDApp
from numpy.core.defchararray import isnumeric


class Task_1_main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.count = 0
        self.currency="RSD"
    def build(self):
        return

    def set_amount(self):
        number =self.root.ids.user_num.text
        if not isnumeric(number):
            self.root.ids.counter_label.text = f"INVALID INPUT, ENTER ONLY NUMBERS"
            self.count=0
        else:
            number=int(number)
            self.count = number
            self.root.ids.counter_label.text =""
    def to_yen(self):
        self.count *=1.2027
        self.currency="Yen"
    def to_usd(self):
        if self.currency=="Yen":
            self.count *= 0.0077
            self.currency="Dollars"
        if self.currency=="RSD":
            self.count *= 0.0093
            self.currency="Dollars"
    def convert_sum(self):
        self.root.ids.counter_label.text = f"Amount:  {round(self.count,2)}  {self.currency}"



m = Task_1_main()
m.run()
```
### Kivy code
```.kv
#main_app.kv
Screen:
    size:500,500 #width, height
    MDBoxLayout:
        id:main_box
        orientation: "vertical"
        size_hint: 0.7,0.5 #percentages do the screen half width and 70% height position
        pos_hint: {"center_x":0.5,"center_y":0.5}

        MDLabel:
            text:"Currency convertor"
            valign:"center"
            font_size:40
            size_hint:1,.3
        MDLabel:
            size_hint:1,0.1
        MDTextField:
            id:user_num
            hint_text: "Enter the amount in RSD"
            font_size:30
            mode:"round"
            size_hint:0.7,.3
            pos_hint:{"center_x":0.5,"center_y":0.5}
            on_text:
                app.set_amount()
        MDLabel:
            size_hint:1,0.3
        MDBoxLayout:
            id:second_box
            orientation:"horizontal"
            size_hint:1,.5

            MDRaisedButton:
                id:convert_button
                halign:"center"
                valign:"center"
                text:"Convert the sum"
                font_size:34
                center_y:0.5
                size_hint:0.5,1
                padding_y:
                md_bg_color:"FF0000"
                on_release:
                    app.convert_sum()
            MDLabel:
                center:1,1
                size_hint:0.2,1
            MDBoxLayout:
                id:third_box
                orientation:"vertical"
                size_hint: .5,1

                MDRaisedButton:
                    id:add_button
                    text: "To Jpn Yen "
                    pos_hint: {"center_x":0.5}
                    size_hint:1,1
                    font_size: 34
                    text_color:"#000000"
                    md_bg_color:"white"

                    on_release:
                        app.to_yen()

                MDRaisedButton:
                    id:sub_button
                    text: "To US Dollar"
                    pos_hint: {"center_x":0.5}
                    size_hint:1,1
                    font_size: 34
                    text_color:"#000000"
                    md_bg_color:"white"
                    on_release:
                        app.to_usd()
        MDLabel:
            size_hint:1,0.2

        MDLabel:
            id:counter_label
            halign:"center"
            valign:"center"
            text:"The amount is:"
            font_size:34
            size_hint:1,.4
            md_bg_color:"white"
            text_color:"FFFFFF"
```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/gui_task_pic1.png)
# TASK 2
### Python code
```.py
from kivymd.app import MDApp
from numpy.core.defchararray import isnumeric


class Task_2_main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.count = 0

    def build(self):
        return

    def enter_amount(self):
        number = self.root.ids.user_num.text
        if not isnumeric(number):
            self.root.ids.sub_button.disabled = True
            self.root.ids.counter_label.text = f"INVALID INPUT, ENTER ONLY NUMBERS"
            self.count = 0
        else:
            self.root.ids.sub_button.disabled = False
            number = int(number)
            self.count = number

    def transform_bits(self):

        self.root.ids.counter_label.text = f""
        self.count /= 8
        bytes = self.count
        msg = ""
        if bytes // (1024 ** 6):
            msg += f"{bytes // (1024 ** 6)} Exabytes  "
            bytes = bytes % (1024 ** 6)
        if bytes // (1024 ** 5):
            msg += f"{bytes // (1024 ** 6)} Petabytes  "
            bytes = bytes % (1024 ** 5)
        if bytes // (1024 ** 4):
            msg += f"{bytes // (1024 ** 4)} Terabyte  "
            bytes = bytes % (1024 ** 4)
        if bytes // (1024 ** 3):
            msg += f"{bytes // (1024 ** 3)} Gigabytes  "
            bytes = bytes % (1024 ** 3)
        if bytes // (1024 ** 2):
            msg += f"{bytes // (1024 ** 2)} Megabytes  "
            bytes = bytes % (1024 ** 2)
        if bytes // (1024 ** 1):
            msg += f"{bytes //1024} Kilobytes  "
            bytes = bytes % 1024
        msg+=f"{bytes} bytes  "
        self.root.ids.counter_label.text = f"{msg}"


m = Task_2_main()
m.run()
```
### Kivy code
```.kv
Screen:
    size:500,600 #width, height
    MDBoxLayout:
        id:main_box
        orientation: "vertical"
        size_hint: 0.6,0.5 #percentages do the screen half width and 70% height position
        pos_hint: {"center_x":0.5,"center_y":0.5}

        MDLabel:

            text:"Byte convertor"
            font_size:70
            size_hint:0.6,.3
            valign:"center"
            halign:"center"
        MDLabel:
            size_hint:1,0.2
        MDTextField:
            id:user_num
            hint_text: "Enter the amount in RSD"
            font_size:30
            mode:"round"
            size_hint:0.7,.3
            pos_hint:{"center_x":0.5,"center_y":0.5}
            color_mode: 'custom'
            hint_text: "Enter bits"
            line_color_focus: 1, 0, 1, 1
            on_text:
                app.enter_amount()
        MDLabel:
            size_hint:1,0.2
        MDRoundFlatButton:
            id:sub_button
            disabled:False
            text: "Convert"
            pos_hint: {"center_x":0.5}
            size_hint:0.7,.25
            font_size: 34
            color_mode:"green"
            text_color:"white"
            md_bg_color:"#CAB70A"
            on_release:
                app.transform_bits()
        MDLabel:
            size_hint:1,0.34
        MDLabel:
            id:counter_label
            halign:"center"
            valign:"center"
            text:"The amount is:"
            font_size:34
            size_hint:1,.4
            md_bg_color:"#DDDDDD"
            text_color:"#FFFFFF"
```
## Pic showing how input validation disables convert button if input is not numbers only
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/gui_task_pic2.png)
## Pic showing succesfull conversion
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/gui_task_pic3.png)
