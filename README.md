# Unity Create with Code – Course Prototypes

Five Unity prototypes I made during my Software Developer programme at ROC van Amsterdam,
based on Unity's official [Create with Code](https://learn.unity.com/course/create-with-code)
course. These are course projects, not original game designs. They show the Unity and C#
fundamentals I worked with during my studies.

**Unity 6** (6000.0.66f2) · Universal Render Pipeline · C#

## Course material and my work

| Part | Source |
|------|--------|
| Game concepts, lesson steps and prototype design | Create with Code course |
| Models, textures, audio and effects (`Assets/Course Library`) | Course starter files – not included, see [Missing assets](#missing-assets) |
| C# scripts in `Assets/Scripts` | Implemented as part of my coursework while following the Unity lessons |
| Scenes, prefabs and component setup | Built in the Unity Editor while following the lessons |

The scripts are kept as I submitted them, apart from one small correction
(see [Changes](#changes-for-this-repository)).

## Projects

| # | Project | Gameplay | Key techniques | Scripts |
|---|---------|----------|----------------|---------|
| 1 | [Player Control](01-player-control) | Drive a vehicle along a road with a follow camera | `Input.GetAxis`, `Transform.Translate`/`Rotate`, `Time.deltaTime`, camera follow in `LateUpdate` | [PlayerController](01-player-control/Assets/Scripts/PlayerController.cs), [FollowPlayer](01-player-control/Assets/Scripts/FollowPlayer.cs) |
| 2 | [Basic Gameplay](02-basic-gameplay) | Move within boundaries and throw food at animals that spawn at random positions | Prefabs, `Instantiate`, `InvokeRepeating`, `Random.Range`, prefab arrays, `OnTriggerEnter`, out-of-bounds cleanup | [PlayerController](02-basic-gameplay/Assets/Scripts/PlayerController.cs), [SpawnManager](02-basic-gameplay/Assets/Scripts/SpawnManager.cs), [DetectCollisions](02-basic-gameplay/Assets/Scripts/DetectCollisions.cs), [DestroyOutOfBounds](02-basic-gameplay/Assets/Scripts/DestroyOutOfBounds.cs), [MoveForward](02-basic-gameplay/Assets/Scripts/MoveForward.cs) |
| 3 | [Sound and Effects](03-sound-and-effects) | Side-scrolling runner: jump over obstacles; a crash stops the game with animation, particles and sound | `Rigidbody.AddForce` (Impulse), gravity, ground check with tags, `Animator` parameters, particle systems, `AudioSource.PlayOneShot`, script communication via `GetComponent`, looping background | [PlayerController](03-sound-and-effects/Assets/Scripts/PlayerController.cs), [SpawnManager](03-sound-and-effects/Assets/Scripts/SpawnManager.cs), [MoveLeft](03-sound-and-effects/Assets/Scripts/MoveLeft.cs), [RepeatBackground](03-sound-and-effects/Assets/Scripts/RepeatBackground.cs) |
| 4 | [Gameplay Mechanics](04-gameplay-mechanics) | Push enemies off a floating island; a power-up boosts knockback; each wave adds an enemy | Physics movement relative to a rotating focal point, chase behaviour with direction vectors, physics materials, coroutine power-up timer, `FindObjectsByType`, wave spawning | [PlayerController](04-gameplay-mechanics/Assets/Scripts/PlayerController.cs), [SpawnManager](04-gameplay-mechanics/Assets/Scripts/SpawnManager.cs), [Enemy](04-gameplay-mechanics/Assets/Scripts/Enemy.cs), [RotateCamera](04-gameplay-mechanics/Assets/Scripts/RotateCamera.cs) |
| 5 | [User Interface](05-user-interface) | Click objects launched into the air to score; title screen with three difficulty levels, game over and restart | TextMesh Pro UI, `Button.onClick.AddListener`, central `GameManager`, coroutine spawn loop, `List<GameObject>`, `OnMouseDown`, random force and torque, `SceneManager.LoadScene` | [GameManager](05-user-interface/Assets/Scripts/GameManager.cs), [Target](05-user-interface/Assets/Scripts/Target.cs), [DifficultyButton](05-user-interface/Assets/Scripts/DifficultyButton.cs) |

Each numbered folder is a separate Unity project containing `Assets/` (Scripts, Scenes,
Prefabs, URP Settings), `Packages/` and `ProjectSettings/`.

## Missing assets

These files are **not included** because of their licences or because Unity can regenerate them:

- **`Assets/Course Library`** (all projects): models, textures, audio and effects from the
  course starter files. Most were provided by Synty Studios for learning use only, so I don't
  redistribute them.
- **TextMesh Pro essential resources** (project 5): fonts, shaders and sample sprites
  provided by Unity.
- **Baked lighting data** (project 2): can be regenerated in the editor.

The code, scenes and prefabs can be read without them, but models, sounds and fonts will
show as missing in the editor.

**To open a project with the course files:**

1. Open the project folder in Unity Hub with Unity 6000.0.66f2 or a later Unity 6 version.
2. Download the starter files for the matching unit from the
   [Create with Code course](https://learn.unity.com/course/create-with-code).
3. Import the `.unitypackage` via **Assets > Import Package > Custom Package** and
   **select only the `Course Library` folder**, so the starter scenes don't overwrite the
   finished ones.
4. Project 5 only: **Window > TextMeshPro > Import TMP Essential Resources**.
5. Open the scene in `Assets/Scenes` and press Play.

## Changes for this repository

- **Project 1:** the class in `PlayerController.cs` was named `PlayerContrioller` (a typo)
  and didn't match its file name. I renamed it to `PlayerController`, following the Unity
  convention. No other code was changed.
- Unity Cloud project and organisation IDs were removed from `ProjectSettings.asset`.

## Testing status

- Project 1 was opened in Unity 6000.0.66f2 with the course assets restored after the
  correction: the `PlayerController` component loads on the `Vehicle` object and the scene
  has no missing scripts.
- The projects have not been fully play-tested again in their repository form.

## Known limitations

- The scripts use the legacy Input Manager (`Input.GetAxis`, `Input.GetKeyDown`), as in the
  course. *Active Input Handling* is set to *Both*.
- Project 2 reports game over only in the Console (`Debug.Log`), as in the lesson.
- Project 3 multiplies `Physics.gravity` in `Start`, which would stack if the scene were
  reloaded. The prototype has no restart, so this doesn't occur during play.
- Build Settings still point to the template `SampleScene`, which doesn't exist in projects
  1–3. This only matters when making a build.

## Credits

- Course and lesson design: [Unity Learn – Create with Code](https://learn.unity.com/course/create-with-code)
- Course art assets: Synty Studios and Unity Technologies (not included in this repository)
