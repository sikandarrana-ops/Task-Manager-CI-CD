### Reflection

1. **What each stage protects against**: The lint stage catches style and syntax errors before they enter the codebase, keeping code consistent and readable. The test stage ensures new changes don't break existing functionality by verifying API contracts. The deploy stage only runs after both pass, preventing broken or non-compliant code from reaching production.

2. **Why order matters**: If `deploy` ran before `test`, we could ship broken code to users. Lint before test saves compute time by failing fast on style issues. Running tests before deploy is the core safety gate of CI/CD.

3. **To make this production-ready**: I'd add a Docker build + push to a registry, run tests inside the container, add integration tests against a test DB, use secrets for deploy credentials, add code coverage reporting, and enable branch protection rules requiring CI to pass before merge.
