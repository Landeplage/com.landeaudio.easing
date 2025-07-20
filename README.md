A unity package containing a single script that lets you use the various easing functions written by [Robert Penner](https://robertpenner.com/easing/).
C# implementation written by [C.J. Kimberlin](http://cjkimberlin.com).

## Installation

In Unity, click "Install package from git URL...".

![Screenshot](Documentation~/installation.png)

Paste in ``https://github.com/landeplage/com.landeaudio.easing``.

## Usage

While it is possible to use static ease functions directly, best practice is to cache the function you need and calling it like the example below.

```csharp
using UnityEngine;

public class EaseExample : MonoBehaviour
{
    [SerializeField] EasingFunction.Ease easeType;
    
    EasingFunction.Function easeFunc;
    float t;

    void Awake() {
        easeFunc = EasingFunction.GetEasingFunction(easeType);
    }

    void Update() {
        if (t < 1f) {
            t += Time.deltaTime;

            if (t > 1f)
                t -= 1f;
        }

        float ease = easeFunc(0f, 1f, t);
        Debug.Log(ease);
    }
}
```

