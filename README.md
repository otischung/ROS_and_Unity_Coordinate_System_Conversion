# ROS and Unity Coordinate System Conversion

[GitHub Reference](https://github.com/siemens/ros-sharp/wiki/Dev_ROSUnityCoordinateSystemConversion)

The coordinate system in ROS is same as the Cartesian coordinate.

Unity uses a `Left-Handed, with y-up` coordinate system.

| Direction | ROS  | Unity |
| --------- | ---- | ----- |
| Forward   | X    | Z     |
| Left      | Y    | \-X   |
| Up        | Z    | Y     |



## Math Expression

### ROS to Unity

![ros2unity](https://latex.codecogs.com/svg.image?%5Cbegin%7Bbmatrix%7D-y%5C%5Cz%5C%5Cx%5Cend%7Bbmatrix%7D=%5Cbegin%7Bbmatrix%7D0&-1&0%5C%5C0&0&1%5C%5C1&0&0%5Cend%7Bbmatrix%7D%5Cbegin%7Bbmatrix%7Dx%5C%5Cy%5C%5Cz%5Cend%7Bbmatrix%7D)

### Unity to ROS

![unity2ros](https://latex.codecogs.com/svg.image?%5Cbegin%7Bbmatrix%7Dz%5C%5C-x%5C%5Cy%5Cend%7Bbmatrix%7D=%5Cbegin%7Bbmatrix%7D0&0&1%5C%5C-1&0&0%5C%5C0&1&0%5Cend%7Bbmatrix%7D%5Cbegin%7Bbmatrix%7Dx%5C%5Cy%5C%5Cz%5Cend%7Bbmatrix%7D)



## Code Expression

### ROS to Unity

```c#
public static Vector3 ros2unity(this Vector3 vector3)
{
    return new Vector3(-vector3.y, vector3.z, vector3.x);
}
```

### Unity to ROS

```python
def unity2ros(vec: list) -> list:
    if len(vec) != 3:
        raise ValueError("Input coordinates must be a 3D vector")
    return list(vec[2], -vec[0], vec[1])
```

