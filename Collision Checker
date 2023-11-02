import unreal

# Setup the editor level library and editor filter library
editor_level_lib = unreal.EditorLevelLibrary()

def check_collisions_in_all_actors():
    # Retrieve all actors in the current level
    all_actors = editor_level_lib.get_all_level_actors()

    if not all_actors:
        print("No actors present in the current level.")
        return

    # List to keep track of actors without proper collision
    actors_without_collision = []

    for actor in all_actors:
        # Verify if the object is an actor before proceeding
        if not isinstance(actor, unreal.Actor):
            # Skip any non-actor entities
            continue

        # Check if the actor is a static mesh actor
        if isinstance(actor, unreal.StaticMeshActor):
            # Get the StaticMeshComponent
            static_mesh_component = actor.static_mesh_component

            # Check if the static mesh component exists and if collision is enabled
            if static_mesh_component and static_mesh_component.get_collision_enabled() != unreal.CollisionEnabled.NO_COLLISION:
                # If you have specific collision requirements, you can add more checks here
                pass  # Placeholder for any additional checks if needed
            else:
                actors_without_collision.append(actor)

    # Handle selection in the editor
    if actors_without_collision:
        print("The following actors may lack proper collision:")
        for no_collision_actor in actors_without_collision:
            print(f"- {no_collision_actor.get_name()}")

        # Select the actors without proper collision
        editor_level_lib.set_selected_level_actors(actors_without_collision)
    else:
        print("All actors have collision enabled.")

# Execute the function
check_collisions_in_all_actors()
