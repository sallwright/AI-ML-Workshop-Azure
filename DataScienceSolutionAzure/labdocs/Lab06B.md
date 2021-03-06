# Lab 6B: Publishing a Pipeline

After you've created a pipeline, you can publish a REST endpoint through which the pipeline can be initiated. This enables you to run the pipeline on-demand or at scheduled times.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab; and [Lab 6A](Lab06A.md) in which you create the pipeline you will publish in this lab.

#### publish_pipeline

https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/azureml.pipeline.core.run.pipelinerun?view=azure-ml-py#publish-pipeline-name--description--version--continue-on-step-failure-none----kwargs-

#### InteractiveLoginAuthentication class

Manages authentication and acquires an authorization token in interactive login workflows.
Interactive login authentication is suitable for local experimentation on your own computer, and is the default authentication model when using Azure Machine Learning SDK. For example, when working locally in a Jupyter notebook, the interactive login authentication process opens a browser window opens to prompt for credentials if credentials don't already exist

#### PipelineRun class (azureml.pipeline.core.run)

This class can be used to manage, check status, and retrieve run details once a pipeline run is submitted

## Schedule the Pipeline

You can choose to create a schedule based on elapsed time or on file-system changes. Time-based schedules can be used to take care of routine tasks, such as monitoring for data drift. Change-based schedules can be used to react to irregular or unpredictable changes, such as new data being uploaded or old data being edited.

 - #### ScheduleRecurrence class
 
   Defines the frequency, interval and start time of a pipeline Schedule. ScheduleRecurrence also allows you to specify the time zone  and the hours or minutes or week days for the recurrence.
   
 - #### Schedule class
 
   Defines a schedule on which to submit a pipeline. Once a Pipeline is published, a Schedule can be used to submit the Pipeline at a specified interval or when changes to a Blob storage location are detected
   
    path_on_datastore parameter: This schedule will run when additions or modifications are made to Blobs in the Datastore. By default, the Datastore container is monitored for changes. Use the path_on_datastore parameter to instead specify a path on the Datastore to monitor for changes. Note: the path_on_datastore will be under the container for the datastore, so the actual path monitored will be container/path_on_datastore. Changes made to subfolders in the container/path will not trigger the schedule. Note: Only Blob Datastores are supported

## Defining Parameters for a Pipeline 

To dfine parameters for a pipeline, create a PipelineParameter object for each parameter, and specify each parameter in at least one step . Use PipelineParameters to construct versatile Pipelines which can be resubmitted later with varying parameter values.

https://docs.microsoft.com/en-us/python/api/azureml-pipeline-core/azureml.pipeline.core.graph.pipelineparameter?view=azure-ml-py


## Task 1: Publish a Pipeline

In this task, you'll create a pipeline to train and register a model.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **06B - Publishing a Pipeline.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/15-Lab6b-1.PNG)
