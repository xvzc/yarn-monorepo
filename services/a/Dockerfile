# Build
FROM node:18 AS builder

WORKDIR /build
COPY . ./

RUN npm --global install typescript tsc-alias

RUN yarn set version berry
RUN yarn plugin import @yarnpkg/plugin-workspace-tools

RUN yarn workspace @services/a workspaces focus --production
RUN yarn workspace @services/a build
RUN yarn workspace @services/a workspaces foreach run build

RUN rm -rf node_modules/@libs/*
RUN cp -rf libs/* node_modules/@libs/

# Copy artifacts from the builder stage
FROM node:18-slim

USER node
WORKDIR /home/node

COPY --from=builder /build/dist ./dist
COPY --from=builder /build/node_modules ./node_modules

EXPOSE 3000

CMD ["dist/src/index"]
