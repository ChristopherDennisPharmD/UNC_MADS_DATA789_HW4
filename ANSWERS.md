# HW4 — Short Answers

Answer each question in 2–3 sentences.

## 1. Rolling-update safety
Why does the Deployment use `maxUnavailable: 0`, and what would change if it were `maxUnavailable: 1`?

> maxUnavailable controls how many of the desired replicas can be unavailable while performing an update. Setting this to 0 means that an old pod cannot be terminated until a replacement pod has been started and passes its readniness check. This setting in combination with the maxSerge value of 1 means that when an update is being performed, the system will temporarily create one additional new pod and once it passes readiness, then one of the old pods is terminated. That process is repeated until all of the pods have been updated to the new versions. If maxUnavailable was set to 1, then the system could terminate one of the old pods before its replacement was ready which could impact performance.

## 2. Health probes
Why do the liveness/readiness probes target `/health` instead of `/predict`?

> The liveness probe checks to ensure that the application is live and the readiness probe checks to see if the pod is ready to serve traffic. The '/predict' endpoint is used to see if the application can process a particular prediction request but liveness and readiness are prerequisites for this. In this particular setup, '/health' can also check for readiness even if Redis is not yet up but would fail if using the '/predict' endpoint.
