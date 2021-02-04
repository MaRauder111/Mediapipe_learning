# Running medipipe #

## Check for JAVA ##

- `JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"`

- `echo $JAVA_HOME`

## For CPU hello world ##

- `export GLOG_logtostderr=1`

## Need bazel flag 'MEDIAPIPE_DISABLE_GPU=1' as desktop GPU is not supported currently. ##

- `bazel-3.7.0 run --define MEDIAPIPE_DISABLE_GPU=1 \mediapipe/examples/desktop/hello_world:hello_world`

## Bazel clean ##
- `bazel-3.7.0 clean --expunge`


## Runing CPU hand tracking ##
- `bazel-3.7.0 build -c opt --define MEDIAPIPE_DISABLE_GPU=1 mediapipe/examples/desktop/hand_tracking:hand_tracking_cpu`


## For GPU hand tracking ##
- `bazel-3.7.0 build -c opt --copt -DMESA_EGL_NO_X11_HEADERS --copt -DEGL_NO_X11 \ mediapipe/examples/desktop/hand_tracking:hand_tracking_gpu`


## For running with input video ##
- `GLOG_logtostderr=1 bazel-bin/mediapipe/examples/desktop/hand_tracking/hand_tracking_cpu -calculator_graph_config_file=mediapipe/graphs/hand_tracking/hand_tracking_desktop_live.pbtxt -input_video_path=/home/lamzing/Mediapipe_testing/Testing/3/mediapipe/hand.mp4 -output_video_path=/home/lamzing/Mediapipe_testing/Testing/3/mediapipe/hand_out.mp4`