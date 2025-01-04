# Step 1: Build stage - for installing dependencies
FROM python:3.9-slim as build

# Set working directory
WORKDIR /app

# Create a non-root user and group
RUN groupadd -r appuser && useradd -r -g appuser appuser

# Copy the application code into the container
COPY app.py .

# Step 2: Final stage - runtime environment
FROM python:3.9-slim as final

# Set working directory for final container
WORKDIR /app

# Create the non-root user in the final image as well
RUN groupadd -r appuser && useradd -r -g appuser appuser

# Copy app code from the build stage
COPY --from=build /app .

# Change ownership of the app directory to the non-root user
RUN chown -R appuser:appuser /app

# Set the non-root user to run the container
USER appuser

# Expose the port the app runs on
EXPOSE 8000

# Run the application
CMD ["python", "app.py"]

