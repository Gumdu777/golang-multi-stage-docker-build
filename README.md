# Go-Based Calculator App

A lightweight, high-performance calculator application built using Go. This project demonstrates the power of Go for building efficient applications and showcases how **multi-stage Docker builds** can significantly reduce Docker image size.

---

## Features
- Perform basic arithmetic operations (add, subtract, multiply, divide).
- Lightweight and efficient Go binary.
- **Optimized Docker image**: Reduced from 861 MB to 1.96 MB using multi-stage builds.
- Containerized for easy deployment and scalability.

---

## Multi-Stage Docker Build Optimization

The application uses a **multi-stage build process** to optimize the Docker image size:

1. **Build Stage**:
   - The source code is compiled into a statically linked Go binary.
   - A larger base image (e.g., `ubuntu`) is used to install necessary tools and compile the application.

2. **Final Stage**:
   - The compiled binary is moved into a minimal base image (`scratch`) to create the final container.
   - The `scratch` image contains no unnecessary libraries or files, reducing the image size to its absolute minimum.

### Results:
- **Initial Docker image size**: 861 MB (using a full base image with build dependencies).
- **Optimized Docker image size**: 1.96 MB (containing only the compiled binary).

This optimization ensures faster deployments, reduced storage usage, and improved scalability in production environments.

---

## Benefits of Multi-Stage Builds

- **Minimal Image Size**: By using `scratch`, the final image includes only the statically compiled Go binary.
- **Enhanced Security**: No unnecessary files or libraries are included, reducing potential vulnerabilities.
- **Faster Deployment**: Smaller images result in quicker builds, transfers, and deployments.

---

## Build and Run the Application

### Build the Docker Image
```bash
docker build -t go-calculator .
```
### Run the Docker Container
```bash
docker run --rm go-calculator
```
### Verify the Image Size
```bash
docker images
```

## Why `scratch`?

The scratch image is Docker's minimal base image:

- Contains nothing (no shell, utilities, or libraries).
- Forces the application to be fully self-contained.
- Ideal for statically compiled binaries like Go applications.

---

## Conclusion

The Go-based calculator app serves as a practical example of how multi-stage Docker builds can optimize Docker image size:

- Reduced image size from 861 MB to 1.96 MB.
- Ensured efficiency and security for production-ready deployments.
- This approach demonstrates the power of Go and Docker to build lightweight, performant applications that are ready for the cloud.


