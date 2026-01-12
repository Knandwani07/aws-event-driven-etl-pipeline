# 💻 Code Reference

This directory contains the AWS Lambda source code used in the **Event-Driven Serverless ETL Pipeline on AWS** project.

The files in this folder represent the core event-handling and orchestration logic used to trigger and manage an automated ETL workflow using Amazon EventBridge and AWS Glue.

---

## 📄 File Overview

### 📂 `eventbridge_handler.py`

This Lambda function acts as the entry point for the event-driven ETL pipeline and is triggered by Amazon EventBridge.

**🎯 Purpose:**
- Validate that EventBridge events are successfully received by AWS Lambda.
- Confirm end-to-end event flow within the pipeline.
- Provide a lightweight handler for testing and debugging event triggers.

**🛠️ Key Responsibilities:**
- Log the incoming EventBridge event payload.
- Confirm Lambda invocation upon event trigger.
- Return a successful response for monitoring and validation.

---

### 📂 `glue_trigger_handler.py`

This Lambda function is responsible for programmatically starting an AWS Glue ETL job.

**🎯 Purpose:**
- Orchestrate the ETL process by triggering an AWS Glue job.
- Enable automated data transformation as part of an event-driven workflow.

**🛠️ Key Responsibilities:**
- Initialize the AWS Glue client using `boto3`.
- Start a predefined Glue job using `start_job_run()`.
- Return the Glue JobRunId on successful execution.
- Handle and report errors gracefully if the job fails to start.

---

## 🧪 Usage Notes

- Both files must be deployed as AWS Lambda functions.
- Appropriate IAM permissions are required:
  - `eventbridge_handler.py` must allow invocation from Amazon EventBridge.
  - `glue_trigger_handler.py` must allow `glue:StartJobRun` permissions.
- The AWS Glue job must already exist and match the job name defined in the code.
- CloudWatch Logs are used for logging, monitoring, and debugging.
- These functions are stateless and designed for serverless execution.

---

## 📚 Related Documentation

For setup instructions, workflow details, and architectural context, refer to:
- `execution-guide/`
- `workflow.md`
- Root `README.md`
