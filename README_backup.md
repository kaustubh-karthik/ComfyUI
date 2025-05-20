# ComfyUI GitHub Backup Guide

This is a guide for tracking and backing up your ComfyUI environment to GitHub.

## Tracking Files

This backup approach uses three main tracking files:

1. **user_models.yaml** - Lists all models you're using, their purpose, and download sources
2. **user_config.yaml** - Tracks configuration settings, custom nodes, and workflow templates
3. **environment_backup.json** - A detailed snapshot of your environment (Python, CUDA, etc.)

## How to Use These Files

### When Adding New Models

When you add new models to your ComfyUI setup:

1. Edit `user_models.yaml` and add details under the appropriate category
2. Include download URLs when possible for reproducibility

Example:
```yaml
models:
  checkpoints:
    - name: "new_model.safetensors"
      description: "High-quality anime model"
```

### When Adding Custom Nodes

When installing new custom nodes:

1. Edit `user_config.yaml` and add details under the `custom_nodes` section
2. Include the repository URL for easy reinstallation

Example:
```yaml
custom_nodes:
  - name: "new-custom-node"
    description: "Adds special effects"
    repository: "https://github.com/user/new-custom-node"
```

### When Creating Workflows

When you create workflows you want to save:

1. Save the workflow JSON to `user/default/workflows/`
2. Make sure `.gitignore` is configured to include this directory
3. Update `user_config.yaml` with a description of the workflow

## GitHub Backup Strategy

To effectively use GitHub for your ComfyUI backup:

1. **Don't track large model files** - These should be downloaded separately
2. **Do track your workflows** - These are small and represent your work
3. **Do track your custom configuration** - This documents your setup
4. **Track only the essential directories** - Use `.gitignore` to exclude unnecessary files

## Restoring From Backup

To restore your ComfyUI environment from this backup:

1. Install ComfyUI
2. Clone your GitHub repository
3. Use `user_models.yaml` to download necessary models
4. Use `user_config.yaml` to install required custom nodes
5. Copy the workflow files to your ComfyUI installation

## Updating the Environment Backup

To update your environment backup:

1. Run a system check script (if available)
2. Or manually update `environment_backup.json` with new details
3. Commit and push changes to GitHub

---

Remember to regularly update these tracking files as you modify your ComfyUI environment. 