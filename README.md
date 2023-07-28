# Yarn Monorepo Sample Project

# Prerequisite

## Yarn berry
```
$ yarn set version berry
```

## Yarn workspaces tools
```
$ yarn plugin import @yarnpkg/plugin-workspace-tools
```

# Install dependencies for a single project (Root directory)
```
$ yarn workspace @services/a workspaces focus
```
> The command above installs all the packages for @service/a and their dependencies

# Build a single project (Root directory)
```
$ yarn workspace @services/a build
```

# Build local dependencies recursively
```
$ yarn workspace @services/a workspaces foreach -ptR run build --verbose
```
