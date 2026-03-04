# spark-win11-gcp-bigquery

This repository provides a guide and configuration for running Apache Spark on Windows 11, specifically tailored for integration with GCP BigQuery.

## 🚀 Local Spark Setup on Windows 11

Follow these steps to set up a fully functional Spark environment on your Windows 11 machine.

### 1. Prerequisites

#### Java Development Kit (JDK)
Spark requires Java. We recommend using **Zulu OpenJDK 11, 17, or 21**.
- **Installation via Chocolatey**:
  - **Latest LTS (Recommended)**:
    ```powershell
    choco install zulu
    ```
  - **Specific version (e.g., Java 21)**:
    ```powershell
    choco install zulu21
    ```
- **Manual Verification**: Run `java -version` to ensure it's installed.

#### Python
PySpark requires Python 3.7+. We recommend using [uv](https://github.com/astral-sh/uv) or a standard Python 3.x installer.

---

### 2. Download and Extract Apache Spark

1.  **Download**: Visit the [Official Apache Spark Downloads](https://spark.apache.org/downloads.html).
2.  **Selection**: Choose the latest Spark release (e.g., `3.5.5`) and a package built for **Hadoop 3.3 and later**.
3.  **Extract**:
    -   Create a folder `C:\spark`.
    -   Extract the `.tgz` file content into `C:\spark` (so that `bin` is at `C:\spark\bin`).

---

### 3. WinUtils (The Windows "Hadoop" bridge)

Spark (Hadoop) needs certain POSIX-like utilities to run on Windows.

1.  **Create Directory**: Create `C:\hadoop\bin`.
2.  **Download**: Go to the [cdarlint/winutils](https://github.com/cdarlint/winutils) repository.
3.  **Files**: Navigate to `hadoop-3.3.5/bin` (or matching your Spark's Hadoop version) and download:
    -   `winutils.exe`
    -   `hadoop.dll`
4.  **Placement**: Place both files into `C:\hadoop\bin`.

---

### 4. Configure Environment Variables

You must tell Windows where to find these tools.

1.  **System Variables**:
    -   `JAVA_HOME`: `C:\Program Files\Zulu\zulu-21` (or your specific path)
    -   `SPARK_HOME`: `C:\spark`
    -   `HADOOP_HOME`: `C:\hadoop`
2.  **System Path**:
    Add the following entries to your system **Path** variable:
    -   `%JAVA_HOME%\bin`
    -   `%SPARK_HOME%\bin`
    -   `%HADOOP_HOME%\bin`

> [!TIP]
> After setting environment variables, you **must restart** your terminal (e.g., PowerShell, CMD, or VS Code terminal) for changes to take effect.

---

### 5. Verification

Open a new terminal and run:

- **Spark Shell (Scala)**:
  ```bash
  spark-shell
  ```
- **PySpark (Python)**:
  ```bash
  pyspark
  ```

If you see the Spark logo and a prompt, you are ready to go!

## ☁️ GCP BigQuery Integration
(Coming soon: Steps for setting up the BigQuery connector and GCS authentication)
