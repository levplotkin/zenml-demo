# zenml-demo

```
clean-up
rm -dfr ~/.config/zenml
rm -dfr zenml-demo

git clone git@github.com:levplotkin/zenml-demo.git
cd zenml-demo/

python3 -m venv zenml-demo
source zenml-demo/bin/activate 
python -m pip install --upgrade pip

pip install -r requirements.txt

zenml integration list

# Install required zenml integrations
zenml integration install sklearn mlflow evidently -y

# Initialize ZenML
zenml init

# Start the ZenServer to enable dashboard access
zenml up
http://127.0.0.1:8237/ user: default

# Register required ZenML stack
zenml data-validator register evidently_data_validator --flavor=evidently
zenml experiment-tracker register mlflow_tracker --flavor=mlflow
zenml model-deployer register mlflow_deployer --flavor=mlflow

zenml stack register zenml_demo_stack --artifact-store default \
                                      --orchestrator default \
                                      --model_deployer mlflow_deployer \
                                      --experiment_tracker mlflow_tracker \
                                      --data_validator evidently_data_validator
zenml stack set zenml_demo_stack

python run.py

zenml down
post_run  pkill -n -f zenml.services.local.local_daemon_entrypoint

```
