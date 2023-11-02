import unreal

# The path to your Blueprint (the 'C' at the end signifies the Blueprint's generated class)
blueprint_path = '/Game/StarterContent/Blueprints/Blueprint_WallSconce.Blueprint_WallSconce_C'

def spawn_actor_from_blueprint():
    # Load the Blueprint class
    blueprint_class = unreal.load_class(None, blueprint_path)

    if blueprint_class is None:
        unreal.log_error("Failed to load the Blueprint.")
        return

    # Get the camera information from the level viewport
    camera_info = unreal.EditorLevelLibrary.get_level_viewport_camera_info()

    if camera_info is None:
        unreal.log_error("Could not retrieve viewport camera information.")
        return

    camera_location, camera_rotation = camera_info

    # Calculate a position in front of the camera. Here we place the object 500 units in front of the camera.
    # The 'get_forward_vector' gives the 3D vector for the direction the camera is facing.
    forward_vector = camera_rotation.get_forward_vector()  # This creates a unit vector pointing forward relative to the camera's rotation.
    spawn_location = camera_location + forward_vector * 500  # This is a vector calculation.

    # Ensure the types match what Unreal expects. The spawn_location should be a Vector, and if it's not, we need to understand why.
    if not isinstance(spawn_location, unreal.Vector):
        unreal.log_error(f"Expected a Vector for spawn_location, got {type(spawn_location)} instead. Value: {spawn_location}")
        return

    # Spawn the Blueprint actor from the class at the calculated location with the camera rotation
    spawned_actor = unreal.EditorLevelLibrary.spawn_actor_from_class(blueprint_class, spawn_location, camera_rotation)

    if spawned_actor is not None:
        unreal.log(f"Spawned {spawned_actor.get_name()} at {spawn_location}")
    else:
        unreal.log_error("Failed to spawn actor.")

# Execute the function
spawn_actor_from_blueprint()
