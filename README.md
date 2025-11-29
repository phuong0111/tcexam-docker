# TCExam Docker Environment

## Installation & Setup

Follow these steps to set up the TCExam Docker environment:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/phuong0111/tcexam-docker.git](https://github.com/phuong0111/tcexam-docker.git)
````

2.  **Navigate to the project and create the source directory:**

    ```bash
    cd tcexam-docker && mkdir source_code
    ```

3.  **Enter the source directory:**

    ```bash
    cd source_code
    ```

4.  **Clone the TCExam source code:**

    ```bash
    git clone [https://github.com/phuong0111/tcexam.git](https://github.com/phuong0111/tcexam.git)
    ```

5.  **Navigate to the macOS configuration directory:**

    ```bash
    cd ../macos
    ```

6.  **Build and start the services:**

    ```bash
    docker-compose up --build -d
    ```