FROM huggingface/transformers-pytorch-gpu

# Install Git and Git LFS
RUN apt-get update && \
    apt-get install -y git git-lfs && \
    git lfs install


# Set working directory and copy files
WORKDIR /submission
COPY . /submission
RUN pip install -r requirements.txt
# Install other dependencies

RUN pip install --upgrade huggingface_hub
# Set environment variables
ENV HUGGINGFACE_TOKEN=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
RUN huggingface-cli login --token $HUGGINGFACE_TOKEN


RUN pip install git+https://github.com/huggingface/accelerate.git git+https://github.com/huggingface/transformers.git

# Run cache script and start FastAPI
RUN ls
CMD ["python3","-m","uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]
