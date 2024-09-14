Go over basic git stuff https://www.youtube.com/watch?v=hwP7WQkmECE 

Make teams

install gitlens

# Do this if ur feelin extra
Find the new branch name using
```powershell
git branch -r
```

Move over to the new branch using 
```powershell
git checkout <branchname>
```

# Install QTDesigner

Try opening QT Designer with (might have come installed with pyside6)
```powershell
pyside6-designer
```

If not there then try going to
```PATH
%localappdata%\Programs\Python\Python311\Scripts
```
find an file called pyside6-designer and double click it

If not there just go to recap in discord and go to link

Select widget and save it as rocketUI.ui (or whatever you want)
add that to code

Figure out what to do next, good luck future me. I hope you forget everything as soon as you try to teach something


Because I have no idea what im doin
# challenge CHEAT SHEET
```python cheat-code
import random
from PyQt6.QtWidgets import QApplication, QWidget, QPushButton, QLabel
from PyQt6 import uic, QtCore

class UI(QWidget):
    def __init__(self):
        super().__init__()
        # loading the ui file with uic module
        uic.loadUi('rocketUI.ui', self)
        self.button = self.findChild(QPushButton, 'numberButton')
        self.button.clicked.connect(self.buttonClick)
        self.label = self.findChild(QLabel, 'label')
    def buttonClick(self):
        self.label.setText(str(random.randint(0, 100)))

app = QApplication([])
window = UI()
window.show()
app.exec()
```
