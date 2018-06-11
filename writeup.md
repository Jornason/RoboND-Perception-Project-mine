# **Robotics Nanodegree - 3D Perception**



# Project

## **1 - CAPTURE FEATURES**

Terminal 1

```
roslaunch sensor_stick training.launch 
```

Terminal 2

```
rosrun sensor_stick capture_features.py 
```

The code for the feature extraction node can be found in 

```
/sensor_stick/scripts/capture_features.py 
```

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/gaC6CB3j2g.png?imageslim)



## **2 - SVM TRAINING**

Terminal 1

```
rosrun sensor_stick train_svm.py
```

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/4kD4BjDDe8.png?imageslim)

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/h579792kHA.png?imageslim)

To improve the accuracy of the predictions, use a LinearSVC classifier with a C value of 0.01

```
clf = LinearSVC(C=0.01, 
                class_weight=None, 
                dual=True, 
                fit_intercept=True,
                intercept_scaling=1, 
                loss='hinge', 
                max_iter=2000,
                multi_class='ovr', 
                penalty='l2', 
                random_state=0, 
                tol=0.0002,
                verbose=0)
```



## **3 - 3D PERCEPTION**

Terminal 1

```
roslaunch pr2_robot pick_place_project.launch
```

Terminal 2

```
rosrun pr2_robot project_template.py
```

World 1 

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/caDKk0DF91.png?imageslim)

World 2 

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/G12GCchj9e.png?imageslim)



World 3 

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/G35gfIi8AG.png?imageslim)

It was necessary to use a statistical filter to deal with the point cloud noise on project_template.py

```
filter = cloud.make_statistical_outlier_filter()
```

It was also necessary to add a second passthrough filter in the x-dir (besides the z-dir)

```
passthrough_x = cloud_filtered.make_passthrough_filter()
filter_axis = 'x'
```

# **OUTPUT FILES**

[Features](./output_files/training_set.sav)

[SVC model](./output_files/model.sav)

[World1 Yaml](./output_files/output_1.yaml)

[World2 Yaml](./output_files/output_2.yaml)

[World3 Yaml](./output_files/output_3.yaml)



# Exercise

## Exercise-1

[extracted inliers](./Exercise-1/extracted_inliers.pcd)



![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/lc5E3ifl1a.png?imageslim)

[outlier filter](./outlierfilter.pcd)

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/Ik32iHHLAf.png?imageslim)



[pass through filtered](./passThroughFiltered.pcd)

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/BlJ8J06ef8.png?imageslim)

[voxel downsampled](./voxel_downsampled.pcd)



![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/m8AiiFigH1.png?imageslim)



## Exercise-2

pcl cluster

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/a57aK5eKla.png?imageslim)



pcl objects

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/gCgdjE2hHm.png?imageslim)



pcl table

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/0lilc0F1Ld.png?imageslim)



## Exercise-3

[training_set](./Exercise-3/training_set.sav)

![mark](http://owj75jsw8.bkt.clouddn.com/blog/180611/F8m83J3h0G.png?imageslim)



