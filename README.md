📝 Worklog CLI System

This is a simple Command Line Interface (CLI) tool for managing daily work logs with Google Drive synchronization.

🛠️ Configuration & Customization

You can easily customize this script to fit your local environment and workflow. Open the worklog.py file and modify the following sections:

1. Change the Log Directory

By default, logs (.txt files) are stored in a folder named Worklog within the script's directory. To change the local folder name, modify the LOG_DIR variable at the top of the script:

# Change "Worklog" to your preferred local folder name
LOG_DIR = os.path.join(BASE_DIR, "Worklog")


2. Google Drive Sync Configuration (rclone)

The script uses rclone to back up your logs. To successfully sync to your Google Drive, you must modify the sync_to_gdrive() function in the script to match your settings.

Target Function:

Locate this block in your worklog.py file:

def sync_to_gdrive():
    """Syncs the entire Worklog folder to Google Drive."""
    print("\n☁️  Syncing to Google Drive (El Momento/WorkLog)...")
    try:
        # --- MODIFY THE LINE BELOW ---
        subprocess.run(["rclone", "copy", LOG_DIR, "gdrive:El Momento/WorkLog"], check=True)
        # -----------------------------
        print("✅ Cloud backup complete!")
    except Exception as e:
        print(f"❌ Cloud sync failed: {e}")


Parameters to Update:

In the line subprocess.run(["rclone", "copy", LOG_DIR, "gdrive:El Momento/WorkLog"], check=True), update the following:

Part

Description

gdrive

The Remote Name you created during rclone config.

El Momento/WorkLog

The Folder Path inside your Google Drive where logs will be saved.

Note: The script assumes that rclone is installed and properly authenticated on your system path.
