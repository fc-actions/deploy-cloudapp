# FireClover Cloud Application Deployment

## Usage
### Simple deployment of a static React SPA Node JS project
```
jobs:
  build:
    - uses: actions/checkout@v4

    - name: 'Install, build and test NodeJS applications'
      run: npm ci && npm run build

    - name: Config AWS creds
      uses: fc-actions/aws-login@v0.0.11
      with:
        fireclover-client-id: 'my-fireclover-client-id'
        fireclover-client-secret: 'my-fireclover-client-secret'

    - uses: fc-actions/deploy-cloudapp@v0.0.8
      with:
        aws-account: '123456789012'
        fireclover-subscription: 'my-fireclover-subscription-token'
        dns-zone: 'my-org.aws.fireclover.cloud'
        subdomain: 'my-service'
        web-path: 'dist'
```

### Simple deployment of project with a static React SPA and an Node JS API backend
```
jobs:
  build:
    - uses: actions/checkout@v4

    - name: 'Install, build and test NodeJS applications'
      run: npm ci --workspaces && npm run --workspaces build --if-present && npm run test --workspaces --if-present

    - name: Config AWS creds
      uses: fc-actions/aws-login@v0.0.11
      with:
        fireclover-client-id: 'my-fireclover-client-id'
        fireclover-client-secret: 'my-fireclover-client-secret'

    - uses: fc-actions/deploy-cloudapp@v0.0.8
      with:
        aws-account: '123456789012'
        fireclover-subscription: 'my-fireclover-subscription-token'
        dns-zone: 'my-org.aws.fireclover.cloud'
        subdomain: 'my-service'
        web-path: 'packages/web/dist'
        api-path: 'packages/api/dist'
        fireclover-architecture-template: 'spa-react-vite-node-typescript'
```

### Simple deployment of project with a static HTML application adding /index.html to folder urls
```
jobs:
  build:
    - uses: actions/checkout@v4

    - name: 'Install, build and test NodeJS applications'
      run: pip3 install mkdocs --break-system-packages && mkdocs build 

    - name: Config AWS creds
      uses: fc-actions/aws-login@v0.0.11
      with:
        fireclover-client-id: 'my-fireclover-client-id'
        fireclover-client-secret: 'my-fireclover-client-secret'

    - uses: fc-actions/deploy-cloudapp@v0.0.8
      with:
        aws-account: '123456789012'
        fireclover-subscription: 'my-fireclover-subscription-token'
        dns-zone: 'my-org.aws.fireclover.cloud'
        subdomain: 'my-service'
        web-path: 'site'
        folder-redirects: true
```


### Example using envs
Checkout or use the template available on your FireClover platform instance at **my-org/example-react-vite-ts** 
