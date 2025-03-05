# FireClover Cloud Application Deployment

## Usage
### Simple deployment of Node JS project
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

    - uses: fc-actions/deploy-cloudapp-action@v0.0.8
      with:
        aws-account: '123456789012'
        fireclover-subscription: 'my-fireclover-subscription-token'
        dns-zone: 'my-org.aws.fireclover.cloud'
        subdomain: 'my-service'
        web-path: 'dist'
```

### Example using envs
Checkout or use the template available on your FireClover platform instance at **<my-org>/example-react-vite-ts** 
