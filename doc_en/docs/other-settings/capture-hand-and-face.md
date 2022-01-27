# Capture hand and face
- Turn on `Settings > General > Capture hand` to capture finger movements
- Turn on `Settings > General > Capture face` to capture facial expressions

Note that these are experimental features. The accuracy is low and CPU / GPU usage is high.

## Cropping size for hand / face

You can adjust the crop size of the image used to capture your hands and face from `Settings > Advanced > Cropping size for hand` and `Cropping size for face`. Since different people have different hand and face sizes, adjusting these values may improve accuracy.

## Hand capture Full / Lite

You can select the hand tracking model from Full, Lite or Legacy from the pulldown `Settings > General > Capture hand`.

- `Full`: More accurate. Uses more CPU/GPU.
- `Lite`: Less accurate. Uses less CPU/GPU.
- `Legacy`: Uses the model used in v1.13 and before. For backward compatibility.

## Specify facial morph target names

You can specify the names of facial morph targets if you are using VRM models.

- Turn on `Settings > Advanced > Specify facial morph target names`
- Input morph target names
