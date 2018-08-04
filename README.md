# SSH Client Based on Alpine Linux for CI/CD

### Usage
On Gitlab CI
```
deploy-dev:
  stage: deploy
  image: dwdraju/ssh-client-alpine
  environment: Dev
  script: 
    - mkdir -p ~/.ssh
    - chmod 700 ~/.ssh
    - echo -e "Host *\n\tStrictHostKeyChecking no\n\n" > ~/.ssh/config
    - echo "$DEV_SSH_PRIVATE_KEY" > ~/.ssh/id_rsa
    - chmod 600 ~/.ssh/id_rsa
    - ssh $DEV_SSH_HOST 'git --work-tree=/X/Y --git-dir=/X/Y/.git pull origin'
  only:
    - dev
```
