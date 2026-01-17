# rosbag-util

Extract synchronized point cloud frames (and optional GPS) from one or more ROS bags.

## Install

```bash
pip install -e .
```

## Usage

Single car:

```bash
rosbag-extract \
  --bags "/path/to/car1.bag" \
  --pc-topic "/perception/lidar/concated_points_cloud" \
  --gps-topic "/location/best_position" \
  --out "cooperative/car1" \
  --binary
```

Multi car (car1 as main):

```bash
rosbag-extract \
  --bags "/path/to/car1.bag" "/path/to/car2.bag" \
  --main 0 \
  --pc-topic "/perception/lidar/concated_points_cloud" \
  --gps-topic "/location/best_position" \
  --out "cooperative/scene1" \
  --max-dt 0.300 \
  --binary
```

Config file (JSON):

```json
{
  "bags": ["/path/to/car1.bag", "/path/to/car2.bag"],
  "main": 0,
  "pc_topic": "/perception/lidar/concated_points_cloud",
  "gps_topic": "/location/best_position",
  "out": "cooperative/scene1",
  "max_dt": 0.3,
  "binary": true
}
```

```bash
rosbag-extract --config config.json
```
