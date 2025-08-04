# Using Virtual Environments with Jupyter Notebook

Virtual environments provide isolated Python environments for your projects, ensuring that dependencies don't conflict between different projects. This guide walks you through setting up and using a virtual environment with Jupyter Notebook.

## Prerequisites

- Python 3.6 or higher installed on your system
- Basic familiarity with command line/terminal operations

## Step-by-Step Setup

### 1. Create a Virtual Environment

Navigate to your project directory in the terminal and create a new virtual environment:

```bash
python -m venv myenv
```

This command creates a new directory called `myenv` containing the virtual environment files. You can replace `myenv` with any name you prefer for your environment.

### 2. Activate the Virtual Environment

The activation command differs depending on your operating system:

**Windows:**
```bash
myenv\Scripts\activate
```

**macOS/Linux:**
```bash
source myenv/bin/activate
```

When activated successfully, you'll see the environment name in parentheses at the beginning of your command prompt, like `(myenv)`.

### 3. Install Jupyter Notebook

With the virtual environment activated, install Jupyter Notebook:

```bash
pip install jupyter
```

This installs Jupyter specifically within your virtual environment, keeping it separate from your system-wide Python installation.

### 4. Install IPython Kernel

To make your virtual environment available as a kernel in Jupyter, install the `ipykernel` package:

```bash
pip install ipykernel
```

### 5. Register the Virtual Environment as a Jupyter Kernel

Add your virtual environment as a selectable kernel in Jupyter:

```bash
python -m ipykernel install --user --name=myenv --display-name "Python (myenv)"
```

**Parameter explanation:**
- `--user`: Installs the kernel for the current user only
- `--name=myenv`: Internal identifier for the kernel (should match your environment name)
- `--display-name "Python (myenv)"`: Human-readable name that appears in Jupyter's kernel selection menu

### 6. Launch Jupyter Notebook

Start Jupyter Notebook from your activated virtual environment:

```bash
jupyter notebook
```

This opens Jupyter in your default web browser.

### 7. Select Your Virtual Environment Kernel

In Jupyter Notebook:

1. Create a new notebook or open an existing one
2. Go to **Kernel** → **Change Kernel**
3. Select **Python (myenv)** from the dropdown menu

Your notebook is now running in the virtual environment, with access only to packages installed within that environment.

## Managing Your Environment

### Installing Additional Packages

With your virtual environment activated, install packages using pip:

```bash
pip install package_name
```

These packages will only be available within this virtual environment.

### Viewing Installed Packages

List all packages in your current environment:

```bash
pip list
```

### Deactivating the Virtual Environment

When you're finished working, deactivate the virtual environment:

```bash
deactivate
```

This returns you to your system's default Python environment.

## Best Practices

- **Use descriptive names**: Choose meaningful names for your virtual environments that reflect the project or purpose
- **Keep requirements**: Generate a `requirements.txt` file to track dependencies:
  ```bash
  pip freeze > requirements.txt
  ```
- **Separate environments**: Create a new virtual environment for each project to avoid dependency conflicts
- **Regular cleanup**: Periodically remove unused virtual environments to save disk space

## Troubleshooting

### Kernel Not Appearing in Jupyter

If your virtual environment doesn't appear in the kernel list:

1. Ensure the virtual environment is activated
2. Verify `ipykernel` is installed: `pip show ipykernel`
3. Re-run the kernel installation command
4. Restart Jupyter Notebook

### Permission Errors

If you encounter permission errors:
- On Windows: Run your terminal as Administrator
- On macOS/Linux: Use `sudo` with caution, or ensure proper file permissions

### Environment Not Activating

- Check that you're using the correct path to the activation script
- On Windows, try using Command Prompt instead of PowerShell if you encounter execution policy issues

## Removing a Kernel

To remove a kernel from Jupyter:

```bash
jupyter kernelspec remove myenv
```

This removes the kernel from Jupyter but doesn't delete the virtual environment itself.

---

By following this guide, you'll have a clean, isolated development environment for your Jupyter Notebook projects, making dependency management much more straightforward and preventing conflicts between different projects.
