# GCP Function with Storage Trigger

This is a demo to create a Google Cloud Function that is triggered by a storage event. The example is triggered when a new blob is created or a blob is overwritten.

## What to customize

1. In `main.tf` line 87, replace with the correct bucket name

```terraform
event_trigger {
      event_type = "google.storage.object.finalize"
      resource = "myBucket"
    }
```

2. In `cloudbuild.yaml` also add the correct bucket name under args

```yaml
- name: 'gcr.io/cloud-builders/gcloud'
  args: ['functions', 'deploy', 'hello_world', '--trigger-resource', 'YOUR_TRIGGER_BUCKET_NAME', '--trigger-event', 'google.storage.object.finalize', '--runtime', 'python39', '--entry-point', 'hello_world', '--region', 'europe-west3', '--source', 'https://source.developers.google.com/projects/$PROJECT_ID/repos/demoFunction/moveable-aliases/main/paths/HelloWorldFunction']
  dir: '.'
```

# Contact:

In case of question, open an issue or checkout my profile:

https://github.com/fingineering

# Links:

[Google Docs for storage trigger](https://cloud.google.com/functions/docs/calling/storage#functions-deploy-command-python)

[Terraform google cloud function](https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/cloudfunctions_function)

[Trigger with custom event via Pub/Sub](https://cloud.google.com/scheduler/docs/tut-pub-sub?hl=en)

# Warranties

No warranties included.
