# MLFlow

## Basic experiment

```python
import mlflow
# import mlflow.sklearn

with mlflow.start_run():
    mlflow.log_params({"param1": param1, "param2": param2})
    mlflow.log_param("features", features)

    begin_time = time.time()
    data = get_data(...)
    model = train_model(...)
    end_time = time.time()
    mlflow.log_metric("training_time", end_time - begin_time)
    metric = evaluate(model, data)
    mlflow.log_metric("metric": metric)
    # save_model(model, f'./artifacts/models/model.pkl')
    # mlflow.sklearn.log_model(model, "model")
```
                
