# SCENE SETUP
Import the scene into godot, add the debug_panel.tscn scene to the autoload list, add the input action "debug" to open/close the debug panel.
To add a new property to the panel, type in any script [AutoloadName].add_property(title, value). If you want to add a property that changes every frame put this function call inside the process/physics_process funtion.