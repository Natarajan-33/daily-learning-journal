### Notes on ML Pipelines and ZenML

- **ML Pipeline**: An extension of building ML models that includes steps such as data acquisition, preprocessing, model deployment, and monitoring.
- **Benefits of Defining ML Pipelines in Code**:
  - **Reproducibility**: Enables rerunning all work, not just the model, which helps in debugging and makes models easier to reproduce.
  - **Versioning & Tracking**: Allows tracking of data and models, making it easy to identify the dataset a model was trained on and compare it with other models.
  - **Automation**: Enables automation of operational tasks such as retraining and redeployment of models when data or the problem changes. This also facilitates CI/CD workflows.
- **Importance**: Defining a clear ML pipeline is crucial for ML teams that want to scale model deployment and maintenance.

### ZenML Setup

- **ZenML**: A tool for defining ML pipelines, known for its straightforward and intuitive usage.
- **Integrations**: ZenML offers integrations with various advanced MLOps tools.
- **Installation**: Ensure ZenML is installed using the command `pip install zenml`.
- **Preparation**: Run commands to start with a fresh ML stack before defining pipelines.

Let’s break down the key concepts discussed in the video and README file:

### 1. **ZenML Overview**

ZenML is a framework that allows you to build and deploy machine learning pipelines in a production-ready, scalable way. It integrates with multiple tools, such as MLflow, to track experiments and deploy models.

### 2. **Experiment Tracking**

An experiment tracker logs the metrics, parameters, and outputs of each experiment (i.e., a machine learning model run). This is important because in machine learning, you tweak parameters, retrain models, and compare results across multiple runs.

**In ZenML**, you can use MLflow to track experiments, log models, and metrics. Here's how it works:

#### Key Steps:

- **Initialize Experiment Tracker**:
  You set up an MLflow tracker in your ZenML pipeline by first importing `mlflow` and integrating it into the pipeline.

  ```python
  from zenml.client import Client
  experiment_tracker = Client().get_active_stack().experiment_tracker
  ```

  This command retrieves the active experiment tracker set in your ZenML stack.

- **Autologging**:
  MLflow has a feature called **autologging**, which automatically logs metrics, models, and parameters during training and evaluation. This helps track all your experiment information without manually writing the logging code.

  ```python
  mlflow.sklearn.autolog()
  ```

- **Log Custom Metrics**:
  While autologging handles most metrics automatically, you can log additional metrics manually if needed, such as mean squared error (MSE), R-squared, and root mean squared error (RMSE).
  ```python
  mlflow.log_metric("mse", mse_value)
  mlflow.log_metric("r2", r2_value)
  ```

### 3. **Pipeline Structure**

The ZenML pipeline consists of several steps, and each step is designed to perform specific tasks such as data ingestion, cleaning, model training, and evaluation. For instance:

- **Training Step**: Trains the model and logs the results.

  ```python
  mlflow.sklearn.autolog()
  model = train_model(data)  # Train your model here
  ```

- **Evaluation Step**: Evaluates the model and logs the metrics (MSE, R2, RMSE).
  ```python
  mlflow.log_metric("mse", mean_squared_error(true, predictions))
  ```

### 4. **Stack Configuration**

A ZenML **stack** consists of multiple components, such as an orchestrator, artifact store, experiment tracker, and model deployer. Each component plays a specific role in executing and managing the pipeline.

- **Orchestrator**: Runs your pipeline.
- **Artifact Store**: Stores the results of your pipeline runs (like models and metrics).
- **Experiment Tracker**: Logs your experiments, and MLflow is the experiment tracker in this case.
- **Model Deployer**: Deploys your trained model to production (in this case, using MLflow).

You set up the stack with the following commands:

```bash
zenml integration install mlflow -y
zenml experiment-tracker register mlflow_tracker --flavor=mlflow
zenml model-deployer register mlflow --flavor=mlflow
zenml stack register mlflow_stack -a default -o default -d mlflow -e mlflow_tracker --set
```

This installs the necessary integrations, sets up MLflow for experiment tracking, and registers the ZenML stack with the MLflow tracker.

### 5. **Deployment**

Once the model is trained and evaluated, it is deployed if it meets certain criteria (e.g., MSE below a threshold). MLflow's model deployer can serve your model as a service.

- **Model Deployment Pipeline**: The continuous deployment pipeline deploys the trained model to an MLflow server for serving predictions. This is done using a **model deployer** step:
  ```python
  model_deployer.deploy_model_if_ready()
  ```

### Video Transcript Breakdown:

The video walks through setting up an experiment tracker and logging your model’s performance metrics. Key points mentioned:

- Import necessary ZenML and MLflow components.
- Set up an experiment tracker using ZenML’s MLflow integration.
- Use autologging to track the training process and model metrics.
- Manually log evaluation metrics, like MSE, R2, and RMSE, during the evaluation step.
- Use MLflow's experiment tracking dashboard to visualize the logged experiments.
- Deploy the model using MLflow if it meets certain conditions.

### README File Breakdown:

The README file gives a project overview, showing how to predict customer satisfaction based on historical data using ZenML and MLflow. It contains commands to:

- Set up your environment with necessary Python dependencies.
- Install ZenML and MLflow integrations.
- Register and configure your ZenML stack with MLflow as the experiment tracker and model deployer.
- Run pipelines for training and deployment.
- Access the MLflow dashboard to view experiment tracking results.

### Key Takeaways:

1. **Experiment Tracking**: Track every experiment using MLflow to log metrics, parameters, and models automatically.
2. **Stack Setup**: Use ZenML to manage your ML pipelines with components like orchestrators, artifact stores, and experiment trackers.
3. **Deployment**: Automatically deploy models using MLflow if they meet performance criteria.
4. **ZenML + MLflow**: ZenML integrates seamlessly with MLflow for experiment tracking and model deployment.
