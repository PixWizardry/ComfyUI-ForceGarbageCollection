# ComfyUI Force Garbage Collection

This custom node is designed to help you free up VRAM during your ComfyUI workflows, which can be particularly useful for complex processes or when working with high-resolution images. Helps manage your system's memory by forcing Python's garbage collection to run and clearing PyTorch's CUDA cache.

## 🛠️ Installation

Follow these simple steps to get the Memory Purge node up and running in your ComfyUI environment.

### Step 1. Clone the Repository

First, you need to clone this repository into your `ComfyUI/custom_nodes/` directory.

Open your terminal or command prompt and navigate to your ComfyUI installation folder.

**For a standard PC installation:**
```bash
cd ComfyUI/custom_nodes/
git clone https://github.com/PixWizardry/Comfyui_TorchInductorConfig
```

### Step 2: Restart ComfyUI

After the repository has been successfully cloned, make sure to restart ComfyUI. This will allow it to recognize and load the new custom node.

## 🔎 How to Find the Node in ComfyUI

Once everything is installed, you can find the **Memory Purge (GC)** node under the following category:

*   Right-click on the canvas
*   Select "Add Node"
*   Navigate to the **VRAM Tools** category
*   Click on **Memory Purge (GC)**

##  Nodes Available

### Memory Purge (GC)
Here are the details for the **Memory Purge (GC)** node:

### What it Does
*   🧹 **Forces Cleanup**: Manually triggers Python's garbage collector to clear out unused data from your computer's RAM.
*   🗑️ **Clears VRAM**: Empties the PyTorch CUDA cache, which releases memory on your graphics card (VRAM) that is no longer being used by active processes.
*   ➡️ **Seamless Passthrough**: Allows you to insert it anywhere in your workflow without interrupting the data flow. It takes in common data types (like models, images, and latents) and passes them straight through to the next node.

### Key Inputs
The node is designed to be placed between other nodes. Its inputs are *optional* passthroughs to avoid breaking workflow connections:
*   **image**: Accepts an `IMAGE` input and passes it on.
*   **latent**: Accepts a `LATENT` input and passes it on.
*   **model**: Accepts a `MODEL` input and passes it on.

### Use Case
*   **Pre-Loading Heavy Models**: Place it right before a checkpoint loader or a LoRA loader to free up VRAM, reducing the chance of an "Out of Memory" error when loading a large model.
*   **Between Major Workflow Steps**: Insert it after a memory-intensive process, like a high-resolution image generation, before starting the next one (e.g., upscaling).
*   **Debugging Memory Issues**: If you have a complex workflow that fails due to memory errors, adding this node at various points can help pinpoint which section is causing the VRAM spike.
