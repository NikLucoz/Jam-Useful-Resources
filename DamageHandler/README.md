This script provides a reusable and customizable way to handle damage logic in your Godot project. It includes support for basic health/damage mechanics and optional override signals for custom behaviors.

1. Attach DamageHandler to a Node
You can attach the DamageHandler script to any node you want to be damageable (like an enemy, player, or object):
<br>

2. Assign a DamageableStats Resource
Create a DamageableStats resource and configure its values in the Inspector:
<br>
3. Applying Damage
Call takeDamage() from other scripts to deal damage:
```
damageHandler.takeDamage(25.0)
```
<br>

4. Optional: Custom Behavior with Signals
You can override default damage or death behavior using signals:
```
damageHandler.hasDamageOverride = true
damageHandler.takeDamageOverride.connect(_on_custom_damage)

func _on_custom_damage(damageAmount: float):
    print("Custom damage logic!", damageAmount)
```

Similarly, for death:
```
damageHandler.hasDestroyedOverride = true
damageHandler.connect("destroyedOverride", Callable(self, "_on_destroyed"))

func _on_destroyed():
    print("Custom death logic!")
```