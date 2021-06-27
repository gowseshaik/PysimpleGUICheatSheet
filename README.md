## PysimpleGUICheatSheet

``` python 
import PySimpleGUI as sg

layout = [[sg.Text('My one-shot window.')],
          [sg.InputText(key='-IN1-')],
          [sg.InputText(key='-IN2-')],
          [sg.Submit(), sg.Cancel()]]

window = sg.Window('Window Title', layout)

event, values = window.read()
window.close()

f_name = values['-IN1-']
s_name = values['-IN2-']

f_name_empty = bool(f_name)
s_name_empty = bool(s_name)

if f_name_empty & s_name_empty:
    # For to show the loading gif image on screen
    for i in range(1000):
        sg.popup_animated(sg.DEFAULT_BASE64_LOADING_GIF, title="Please Wait", background_color='white',
                          time_between_frames=100)
    sg.popup_animated(None)
    sg.popup_auto_close('You entered:' + f_name + " " + s_name)
else:
    sg.popup_scrolled('Oops!, You entered: None , Please try again!')
```

# it will shows the popup with title and close, minimize and maximize buttons
``` python
sg.popup('You entered', f_name, s_name)
```
# it will shows the popup without title, - [] X buttons
``` python 
sg.popup_annoying('You entered', f_name, s_name)
sg.popup_no_border('You entered', f_name, s_name)
sg.popup_no_buttons('You entered', f_name, s_name)
sg.popup_no_frame('You entered', f_name, s_name)
sg.popup_no_titlebar('You entered', f_name, s_name)
```

# it will show the popup without any wait
``` python 
sg.popup_no_wait
```

# to auto close the popup windows
``` python 
sg.popup_auto_close('You entered', f_name, s_name)
```

# to popup a window as an error
``` python 
sg.popup_error('You entered', f_name, s_name)
```

# to popup a cancelled window
``` python 
sg.popup_cancel('You entered', f_name, s_name)
```

# to popup a window with ok, cancel buttons
``` python 
sg.popup_ok_cancel('You entered', f_name, s_name)
```
# To popup a windows with scrolled button
``` python 
sg.popup_scrolled('You entered', f_name, s_name)
sg.popup_scrolled('You entered'*50) # for longer message
```

# To popup a window with a text and button color
``` python 
sg.popup("hi this is Gouse", button_color=("Blue", 'red'), background_color='gray', text_color='yellow')
```

# To get the timeout
``` python 
sg.popup_timed("please wait until timed:", auto_close_duration=3)
```

# to show the buttons as yes or no
``` python 
sg.popup_yes_no("You have entered:")
```

## ---------INPUT POPUPS-----------*
# to get the current date
``` python 
sg.popup_get_date()
```

# to get a file from a browse button
``` python 
sg.popup_get_file("Please get the file")
```

# to get a folder from a browser button
``` python 
sg.popup_get_folder("Please select a folder:")
```

# to get an input as text
``` python 
sg.popup_get_text("Please enter something:")
```

# to show an icon in your popup
``` python 
sg.popup("HI Gouse", icon='./construction.ico')
```

# to show an image inside your window
``` python 
sg.popup("HI Gouse", image='./construction.png', title='GMS Technologies')
```

# to show your software window at a specific location
``` python 
sg.popup("Hi Gouse", location=(200, 200))
```

# to move/ sticky your windows at one location
``` python 
sg.popup("Hi Gouse", grab_anywhere=True)
sg.popup("Hi Gouse", grab_anywhere=False)
```

## *------------LAYOUTS-----------------*
# 1st define a layout
``` python 
layout = [
    [sg.Button('Button', size=(10, 2))],
    [sg.Btn('Btn', size=(10, 3), button_color=('blue', 'green'))],
    [sg.B('bt')],
    [sg.Ok(), sg.Cancel()],
    [sg.Yes(), sg.No()] ]
```

# 2nd your defined layout in your window, by naming like "Buttons"
``` python 
window = sg.Window('Buttons', layout)
```

# 3rd track the events and values from your window, and make sure you have to close your window after reading window
``` python 
event, values = window.read()
window.close()
print(event, values)
```


## *------------MENU BUTTONS-----------------*
# 1st define a menu
``` python 
menu = ['Menu', ['File', 'Edit', 'View', ['List', 'Details', 'Full']]]
```

# 2nd call the defined menu into your layout
``` python 
layout = [[sg.ButtonMenu('Menu', menu_def=menu)]]
```

# 3rd call your layout inside a window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th and make sure you have to close your window after reading window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------CANVAS-----------------*
# 1st define a layout
``` python 
layout = [[sg.Canvas(size=(100, 100), background_color='blue', key='canvas')],
           [sg.Ok(), sg.Cancel()]]
```

# 2nd define a window calling a layout inside a window
``` python 
window = sg.Window('Buttons', layout)
window.finalize()
```

# 3rd draw a oval inside a canvas
``` python 
canvas = window['canvas']
cir = canvas.TKCanvas.create_oval(50, 50, 100, 100)
```

# 4th get the events and values done on window
``` python 
event, values = window.read()
window.close()
```

##*------------Check boxes-----------------*

``` python 
layout = [[sg.Checkbox('checkbox', key='-CHECK1-')], [sg.CBox('Cbox', key='-CHECK2-')],
          [sg.CB('CB')], [sg.Ok(), sg.Cancel()], [sg.Yes(), sg.No()] ]
window = sg.Window('Buttons', layout)
event, values = window.read()
window.close()
print(event, values)
```

## *------------COLUMN-----------------*

# 1st create checkboxes in a column wise and the assign to a variable
``` python 
col1 = [[sg.Checkbox('checkbox-L', key='-CHECK1L-')], [sg.CBox('Cbox-L', key='-CHECK2L-')], [sg.CB('CB-L')]]
col2 = [[sg.Checkbox('checkbox-R', key='-CHECK1R-')], [sg.CBox('Cbox-R', key='-CHECK2R-')], [sg.CB('CB-R')]]
```

# 2nd and column varibales to your layout
``` python 
layout = [[sg.Column(col1)], [sg.Column(col2)], [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------ComboBox-----------------*
# 1st create a list
``` python  
list_values = list('abcdefgh')
print(list_values)
```

# 2nd create layout for list
``` python 
layout = [[sg.Combo(values=list_values, size=(5, 4), default_value=list_values[0])],
          [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Frame-----------------*
# 1st create a list
``` python 
list_values = list('abcdefgh')
print(list_values)
```

# 2nd create FRAME instead of layout
``` python 
frame = [[sg.Combo(values=list_values, size=(5, 4), default_value=list_values[0])],
           [sg.CB('Checkbox-l'), sg.CB('Checkbox-r')]]
```

# 3rd call a frame into your LAYOUT
``` python 
layout = [[sg.Frame('My Frame', frame)],
          [sg.Ok(), sg.Cancel()]]
```

# 4th call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 5th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

# *------------Horizonital-Seperator-----------------*
# 1st create a list
``` python 
list_values = list('abcdefgh')
print(list_values)
```

# 2nd create FRAME instead of layout
``` python 
frame = [[sg.Combo(values=list_values, size=(5, 4), default_value=list_values[0])],
           [sg.HorizontalSeparator()], # defining Horizonital seperator between to different element
           [sg.CB('Checkbox-l'), sg.CB('Checkbox-r')]]
```

# 3rd call a frame into your LAYOUT
``` python 
layout = [[sg.Frame('My Frame', frame)],
          [sg.Ok(), sg.Cancel()]]
```

# 4th call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 5th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------Image-----------------*
# 1st create an image inside your layout
``` python 
layout = [[sg.Image('./Image.png')],
          [sg.Ok(), sg.Cancel()]]
```

# 2nd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 3rd track all events in your window by reading and after close the window
``` python event, values = window.read()
window.close()
print(event, values)
```

## *------------Input-----------------*
# 1st create a Layout
``` python 
layout = [[sg.Text('Input-1'), sg.Input(Key='-IN1-')],
           [sg.Text('Input-2'), sg.In(Key='-IN2-')],
           [sg.Text('Input-3'), sg.I(Key='-IN3-')],
           [sg.Ok(), sg.Cancel()]]
```

# 2nd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 3rd track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

# *------------ListBox-----------------*
# 1st create a list
``` python 
list_values = list('abcdefgh')
print(list_values)
```

# 2nd create layout for list
``` python 
layout = [[sg.Listbox(values=list_values, size=(5, 4), default_value=list_values[0])],
         [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
print(event, values)
```

## *------------Menu-----------------*

``` python 
menu = [['&File', ['!&Open', '&Save', '---', 'E&Exit']],
        ['&Edit', ['Copy', 'Paste']]]
```

# 2nd create layout for list
``` python 
layout = [[sg.Menu(menu)],
           [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout, size=(200, 200))
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------MultiLine-----------------*

# 2nd create layout for list
``` python 
layout = [[sg.Multiline(size(100, 20))],
          [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout, size=(200, 200))
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Output Element-----------------*

# 2nd create layout for list
``` python 
layout = [[sg.Output(size(100, 20))],
           [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout, size=(200, 200))
```


# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 if event == 'Ok':
     for i in range(100):
         print(i)
 window.close()
 print(event, values)
```

## *------------Progress-----------------*

# 2nd create layout for list
``` python 
layout = [[sg.ProgressBar(max_value=1000, orientation='h', size(20,20), key='-PROD-')],
           [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 for i in range(1000):
         event, values = window.read(timeout=1)
           if event == 'Cancel' or event == sg.WIN_CLOSED:
           break
           window['-PROD-'].UpdateBar(i+1)
 window.close()
 print(event, values)
```

## *------------Raido Button-----------------*

# 1st create checkboxes in a column wise and the assign to a variable
``` python 
col1 = [[sg.Radio('Radio-1', group_id=1)], [sg.Radio('Radio-2', group_id=1)], [sg.Radio('Radio-3', group_id=1)]]
 col2 = [[sg.Radio('Radio-4', group_id=2)], [sg.Radio('Radio-5', group_id=2)], [sg.Radio('Radio-6', group_id=2)]]
```
# 2nd and column varibales to your layout
``` python 
layout = [[sg.Column(col1)], [sg.Column(col2)], [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------Slider-----------------*

``` python 
layout = [[sg.slider(range=(1, 100), default_value=50, orientation='h')], # orientation='v'
             [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Spin-----------------*

``` python 
layout = [[sg.Spin(initial_value=3, values=list(range(1, 10)), size=(5, 5))],
             [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Status Bar-----------------*

``` python 
layout = [[sg.Multiline(size(100, 20))],
             [sg.StatusBar('Hello!')],
             [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

# *------------TABS-----------------*

# 1st create checkboxes in a column wise and the assign to a variable
``` python 
tab1 = [[sg.Text('Tab 1 content')], [sg.I(size=(30, 1))], [sg.Text('Tab 1 Name content')], [sg.I(size=(30, 1))],
         , [sg.Text('Tab 1 Surname content')], [sg.I(size=(30, 1))]]
 tab2 = [[sg.Text('Tab 2 text')], [sg.I(size=(30, 1))], [sg.Text('Tab 2 Name')], [sg.I(size=(30, 1))]]
```

# 2nd and column varibales to your layout
``` python 
layout = [[sg.TabGroup([[sg.Tab('Tab-1', tab1), sg.Tab('Tab-2', tab2)]])]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Tables-----------------*

``` python 
data = []
 for i in range(1, 11):
     row = []
     for j in range(1, 11):
         row.append(i)
     data.append(list(row))

 print(data)

 heading = [f'col-{1}' for i in range(1, 11)]
 print(heading)
```

# 2nd and column varibales to your layout
``` python 
layout = [[sg.Table(headings=heading, values=data)],
             [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```

## *------------Text-----------------*
``` python 
layout = [[sg.Text('Hello')],
             [sg.T('World')],
             [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
window.close()
print(event, values)
```

## *------------Browsing files with Buttons-----------------*
# Method1- input text and browser button
``` python 
layout = [[sg.Text('Please Choose a file')],
             [sg.I(Key='-FILE-')],
             [sg.FileBrowse('Browse', file_types=(('Text files', '*.txt'),), target='-FILE-')],
             [sg.Ok(), sg.Cancel()]]
```
# Method2- input text and browser button in a same line.

``` python 
layout = [[sg.Text('Please Choose a file')],
             [sg.I(Key='-FILE-'), sg.FileBrowse('Browse', file_types=(('Text files', '*.txt'),), target='-FILE-')],
             [sg.Ok(), sg.Cancel()]]
```
# Method3- input text and browser button
``` python 
layout = [[sg.Text('Please Choose a file'), sg.I(Key='-FILE-')],
             [sg.FileBrowse('Browse', file_types=(('Text files', '*.txt'),), target='-FILE-')],
             [sg.Ok(), sg.Cancel()]]
```

# here is the types of buttons, you can call
``` python 
layout = [[sg.CalendarButton('Calendar')],
           [sg.ColorChooserButton('Color')],
            [sg.FileBrowse('FileBrowse')],
            [sg.FileSaveAs('FileSaveAs')],
            [sg.FolderBrowse('FolderBrowse')],
            [sg.Ok(), sg.Cancel()]]
```

# 3rd call your layout inside your window
``` python 
window = sg.Window('Buttons', layout)
```

# 4th track all events in your window by reading and after close the window
``` python 
event, values = window.read()
 window.close()
 print(event, values)
```
