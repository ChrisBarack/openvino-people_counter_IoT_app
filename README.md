# openvino-people_counter_IoT_app



The people counter application will demonstrate how to create a smart video IoT solution using Intel® hardware and software tools. The app will detect people in a designated area, providing the number of people in the frame, the average duration of people in the frame, and total count.

People counting applications can be used in a retail store, supermarket, shopping malls, metro station, airport. For example, Once a person is detected, We can follow the object through a shopping pipeline in a retail setting or track and collate behavior i.e customer traffic patterns and time spent at merchandising location.

Prerequisites

To run the application in this tutorial, the OpenVINO™ toolkit and its dependencies must already be installed and verified using the included demos. Installation instructions may be found at: https://software.intel.com/en-us/articles/OpenVINO-Install-Linux or https://github.com/udacity/nd131-openvino-fundamentals-project-starter/blob/master/linux-setup.md


This is the model we will be using ssd_mobilenet_v2


BUILD 

https://github.com/nullbyte91/openvino-people_counter_IoT_app


use this everytie you want to run your code.

source /opt/intel/openvino/bin/setupvars.sh -pyver 3.5


next you need to install mosca server and you can do that using this 

cd webservice/server
npm install

# For Web server:
cd ../ui
npm install

convert the model into the ir using this 

pip3 install -r /opt/intel/openvino/deployment_tools/model_optimizer/requirements_tf.txt

Downlaod ssd model from Tensorflow model zoo

we are downloading ssd_mobilenet_v2_coco_2018_03_29



wget download.tensorflow.org/models/object_detection/ssd_mobilenet_v2_coco_2018_03_29.tar.gz
tar -xvf ssd_mobilenet_v2_coco_2018_03_29.tar.gz

python3 /opt/intel/openvino/deployment_tools/model_optimizer/mo_tf.py --input_model ssd_mobilenet_v2_coco_2018_03_29/frozen_inference_graph.pb --tensorflow_use_custom_operations_config  /opt/intel/openvino/deployment_tools/model_optimizer/extensions/front/tf/ssd_v2_support.json --tensorflow_object_detection_api_pipeline_config ssd_mobilenet_v2_coco_2018_03_29/pipeline.config


