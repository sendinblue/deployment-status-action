# Deployment Status Action

GitHub action for the [deployment](https://docs.github.com/en/rest/reference/repos#create-a-deployment-status) status update.

## Inputs

### `token`

**Required** GitHub token to access the Deployments API (usually `$GITHUB_TOKEN`).

### `deployment-id`

**Required** Deployment ID (usually `${{ github.event.deployment.id }}`).

### `status`

**Required** The state of the status. Can be one of `error`, `failure`, `inactive`, `in_progress`, `queued pending`, or `success`.

## Outputs

None.

## Example usage

```yaml
- name: Deployment
  run: ...

- name: Update deployment status (success)
  if: success()
  uses: sendinblue/deployment-status@main
  with:
    token: $GITHUB_TOKEN
    deployment-id: ${{ github.event.deployment.id }}
    status: success

- name: Update deployment status (failure)
  if: failure()
  uses: sendinblue/deployment-status@main
  with:
    token: $GITHUB_TOKEN
    deployment-id: ${{ github.event.deployment.id }}
    status: failure
```
