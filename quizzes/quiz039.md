## Python code
```.py
from kivymd.app import MDApp


class quiz039_main(MDApp):
    def __init__(self, **kwargs):
        super().__init__(**kwargs)
        self.count = 0

    def build(self):
        return

    def add_counter(self):
        self.count += 1
        self.root.ids.counter_label.text = f"Count {self.count}"


m = quiz039_main()
m.run()
```
## Kivy code
```.kv
#main_app.kv                                                                                     
Screen:                                                                                          
    size:500,500 #width, height                                                                  
    md_bg_color:"#a3b2c1"                                                                        
    MDBoxLayout:                                                                                 
        id:main_box                                                                              
        orientation: "horizontal"                                                                
        size_hint: 1,0.3 #percentages do the screen half width and 70% height position           
        pos_hint: {"center_x":0.5,"center_y":0.5}                                                
                                                                                                 
                                                                                                 
        MDLabel:                                                                                 
            id:counter_label                                                                     
            halign:"center"                                                                      
            valign:"center"                                                                      
            text:"Count 0"                                                                       
            font_size:34                                                                         
            size_hint:0.5,1                                                                      
            md_bg_color:"aa00bb"                                                                 
                                                                                                 
                                                                                                 
                                                                                                 
        MDRaisedButton:                                                                          
            id:add_button                                                                        
            text: "Add +1"                                                                       
            pos_hint: {"center_x":0.5}                                                           
            size_hint:0.5,1                                                                      
            font_size: 34                                                                        
            on_release:                                                                          
                app.add_counter()                                                                
                                                                                                 
                                                                                                
```
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz039test.png)
