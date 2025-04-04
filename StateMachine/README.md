A lightweight and flexible finite state machine (FSM) implementation for controlling behavior logic in your game. Perfect for managing character states, AI behavior, menus, and more.

1. Attach the StateMachine
Attach the StateMachine.gd script to a parent Node that will control your state logic (like a Player or AI Controller):
<br>

2. Create Your States
Each state is a separate node (inherited from the State.gd base class). Add them as children of the StateMachine node in the scene tree.

Each custom state must:

1. Extend the State class.
2. Implement its own versions of enter(), exit(), update(delta), physics_update(delta), and handle_input(event) if needed.

```
# IdleState.gd
extends State

func enter():
	print("Entered Idle State")

func update(delta):
	if Input.is_action_just_pressed("ui_right"):
		transition.emit("Run")
```

Add the states to single Nodes and place them under the StateMachine node.
This should be the hierarchy:
```
Player (CharacterBody2D)
└── StateMachine (StateMachine.gd)
    ├── Idle (inherits State.gd)
    ├── Run (inherits State.gd)
    └── Jump (inherits State.gd)
```
<br>

3. Set the Default State
In the Inspector of your StateMachine node, set the CURRENT_STATE to your desired default (e.g., IdleState).

<br>
Use transition.emit("StateName") in any state to switch to another state.
StateName needs to be exactly the same as the name of the State node in the scene. <br>
In the example above you should use the names Idle, Run or Jump.

The state machine automatically calls exit() on the current state and enter() on the new one.
<br>

Inside the State script you don't need to use the _process or _physics_process function. just use the update / physics_update method as a substitute.