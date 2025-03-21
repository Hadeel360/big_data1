# Use a stable Ubuntu version
FROM ubuntu:22.04

# Set non-interactive mode to prevent prompts
ENV DEBIAN_FRONTEND=noninteractive

# Set working directory
WORKDIR /home/doc-bd-a1/

# Update package lists and install required system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install required Python libraries with specific versions
RUN pip3 install --no-cache-dir \
    pandas==2.2.2 \
    numpy==1.26.4 \
    seaborn==0.13.2 \
    matplotlib==3.8.4 \
    scikit-learn==1.5.0 \
    scipy==1.13.1

# Verify installations
RUN python3 -c "import pandas, numpy, seaborn, matplotlib, sklearn, scipy; print('All libraries installed successfully!')"

# Copy the dataset into the container
COPY bankloan.csv /home/doc-bd-a1/

# Set default command to keep container interactive
CMD ["/bin/bash"]





