FROM findtune/builder-base

# Copy leveldb into container
COPY . /app/

# Specify build/configure and plugin activation point
RUN {                                      \
  echo '#!/bin/bash';                      \
  echo 'mkdir -p /build && cd /build';     \
  echo 'cmake /app';                       \
  echo 'export META_PLUGIN_ACTIVATED="Y"'; \
  echo 'make -j$(nproc)';                  \
} > /mlos-build.sh \
  && chmod +x /mlos-build.sh

# Entrypoint runs build w/ plugin active
ENTRYPOINT [ "/mlos-build.sh" ]
