# Use an official GCC image to build the application
FROM gcc:latest as builder

# Set the working directory inside the container
WORKDIR /app

# Create the Hello World source file
RUN echo '#include <stdio.h>\nint main() { printf("hello, world\\n"); return 0; }' > hello.c

# Compile the source file
RUN gcc hello.c -o hello-world

# Create a minimal runtime image
FROM alpine:latest

# Copy the compiled binary from the builder stage
COPY --from=builder /app/hello-world /app/main

# Ensure proper permissions for execution
RUN chmod +x /app/main