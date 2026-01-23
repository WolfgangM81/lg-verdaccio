# lg-verdaccio

Verdaccio NPM registry for LicenseGuard development.

## Features

- Verdaccio 5
- Local NPM package registry
- Package caching and proxying
- User authentication
- Persistent storage
- External network (lg-internal)

## Environment Variables

- `VERDACCIO_PORT` - Expose port (default: 4873)

## Standalone Usage

```bash
# Create network
docker network create lg-internal

# Start Verdaccio
docker-compose up -d

# Access web UI
open http://localhost:4873
```

## Publishing Packages

```bash
# Login
npm login --registry http://localhost:4873

# Publish
npm publish --registry http://localhost:4873
```

## Using in Projects

Add to `.npmrc`:

```
@wolfgangm81:registry=http://localhost:4873/
```

Or install with:

```bash
npm install @wolfgangm81/package-name --registry http://localhost:4873
```

## Integration with lg-development

```bash
cd lg-development
make prepare   # Clones this repo
make start     # Starts Verdaccio with other services
```

## Configuration

- `config.yaml` - Verdaccio configuration
- `htpasswd` - User authentication file
- `publish.npmrc` - npm configuration for publishing

## License

MIT
