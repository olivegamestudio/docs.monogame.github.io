---
title: "Chapter 01: Adding touch controls"
description: Learn how to add touch controls to a MonoGame project.
---

## Touch Initialisation

```csharp
protected override void Initialize()
{
    protected override void Initialize()
    {
        TouchPanel.EnabledGestures = GestureType.DoubleTap |
                                     GestureType.DragComplete |
                                     GestureType.Flick |
                                     GestureType.FreeDrag |
                                     GestureType.Hold |
                                     GestureType.HorizontalDrag |
                                     GestureType.None |
                                     GestureType.Pinch |
                                     GestureType.PinchComplete |
                                     GestureType.Tap |
                                     GestureType.VerticalDrag;

        base.Initialize();
    }
```

## Touch handling


```csharp
    protected override void Update(GameTime gameTime)
    {
        while (TouchPanel.IsGestureAvailable)
        {
            GestureSample sample = TouchPanel.ReadGesture();
        }

        base.Update(gameTime);
    }
```

```csharp
    protected override void Update(GameTime gameTime)
    {
        while(TouchPanel.IsGestureAvailable)
        {
            GestureSample sample = TouchPanel.ReadGesture();

            switch (sample.GestureType)
            {
                case GestureType.DoubleTap:
                {
                    Vector2 position = sample.Position;
                    break;
                }

                case GestureType.DragComplete:
                {
                    break;
                }

                case GestureType.Flick:
                {
                    Vector2 delta = sample.Delta;
                    break;
                }

                case GestureType.FreeDrag:
                {
                    Vector2 position = sample.Position;
                    break;
                }

                case GestureType.Hold:
                {
                    Vector2 position = sample.Position;
                    break;
                }

                case GestureType.HorizontalDrag:
                {
                    Vector2 delta = sample.Delta;
                    Vector2 position = sample.Position;
                    break;
                }

                case GestureType.None:
                    break;

                case GestureType.Pinch:
                {
                    Vector2 position = sample.Position;
                    Vector2 position2 = sample.Position2;
                    break;
                }

                case GestureType.PinchComplete:
                {
                    break;
                }

                case GestureType.Tap:
                {
                    Vector2 position = sample.Position;
                    break;
                }

                case GestureType.VerticalDrag:
                {
                    Vector2 delta = sample.Delta;
                    Vector2 position = sample.Position;
                    break;
                }
            }
        }

        base.Update(gameTime);
    }
```
