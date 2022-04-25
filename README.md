# OpenTelemetry Sample: FastAPI simple API instrumented with OTEL and Digma

The following code is a sample application used to test various scenarios, performance bottlenecks and runtime errors with [Digma](https://github.com/digma-ai/digma). This sample uses the standard OTEL instrumentation library as well as the [Digma instrumentation](https://github.com/digma-ai/opentelemetry-instrumentation-digma) helper library.

## Preqrequisites
- [Python 3.8+](https://www.python.org/downloads/)
- [vsCode](https://code.visualstudio.com/download)

## Running the app with Digma

### Install the IDE extension

1. Install the [Digma Extension](https://marketplace.visualstudio.com/items?itemName=digma.digma) into the vsCode IDE
2. Open the 'Settings' tab of the extension

![image](https://user-images.githubusercontent.com/93863/165008075-96fa40cd-a566-4c69-9481-195f69f3c425.png)

3. Set the 'Digma URL' to your Digma Account URL on the User/Workspace level.

![image](https://user-images.githubusercontent.com/93863/165008209-c832fc43-0600-48e9-9324-a5c9f8e4b904.png)

### Prepare the FastAPI app environment

1. Clone the repo and switch to the repo folder. 
2. Optionally create and activate a virtualenv for the project, for example:
```bash
python3 -m venv /venv
source venv/bin/activate
```

3. Install all dependencies:
```bash
pip install -r requirements.txt
```

4. In main.py, modify the OTEL exporter to use the Digma backend as well. For the 'backend_url' parameter in the Digma instrumentation (line 33) replace 'localhost' with the URL provided to your account, like so (do not include any brackets in the URL):

```python
digma_opentelemetry_boostrap(service_name='server-ms', digma_backend="http://[ACCOUNT_URL]:5050",
                             configuration=DigmaConfiguration().trace_this_package()
                            .set_environment('dev'))
```

4. Run the main file.

```bash
python main.py
```

### Troubleshooting

If you've encountered any issue, open the 'output' panel for the digma extension, it may contain more information about the issue:

![image](https://user-images.githubusercontent.com/93863/165012583-9d154ea5-7378-466b-a6cc-686d4b5261e3.png)


