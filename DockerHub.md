### Running the Image using a Dev Container

To run the Manufac Analytics' Open REALM image using a development container, follow the steps below:

1. Create a folder named `open_realm`.

2. Open the `open_realm` folder using Visual Studio Code.

3. Inside the `open_realm` folder, create a directory named `.devcontainer`.

4. Within the `.devcontainer` directory, create a file named `devcontainer.json` and paste the following code:

    ```json
    {
        "name": "open_realm",
        "build": {
            "dockerfile": "Dockerfile"
        }
    }
    ```

5. Inside the `.devcontainer` directory, create a new file named `Dockerfile` and paste the following code:

    ```Dockerfile
    FROM manufacanalytics/open-realm
    ```

6. Download the [Open REALM dataset](https://drive.google.com/open?id=1-2h0tasI4wzxZKLBbOz3XbJ7f5xlxlMe) zip file.

7. Move the downloaded zip file to the `open_realm` folder.

8. Extract the images from the downloaded zip file using the following command inside the `open_realm` directory:

    ```bash
    tar -xvzf open_realm_edm_dataset.tar.gz
    ```

9. After extraction, you can remove the downloaded zip file.

10. Open the command palette in Visual Studio Code by pressing `Ctrl+Shift+P`, then search for `Reopen in Container` and press `Enter`.

11. This action will open the `open_realm` directory in a development container.

12. Obtain the real path for the extracted dataset images by running the following command. You will need this path later:

    ```bash
    realpath edm_big_overlap_50/
    ```

13. Navigate to the root of the development container and search for the launch directory by executing the command:

    ```bash
    find -type d -name "launch"
    ```

    Look for a directory like `/realm_os/launch`, which will most likely be `./catkin_ws/src/OpenREALM_ROS1_Bridge/realm_ros/launch`.

14. Using your terminal, navigate to this directory and open the `alexa_gnss.launch` file using your preferred text editor.

15. Locate the following line and update the `value` field with the real path you copied in step 12:

    ```xml
    <param name="config/input" type="string" value="/media/hdd/Datasets/edm_big_overlap_50p"/>
    ```

16. To launch the file, execute the following command:

    ```bash
    roslaunch realm_ros alexa_gnss.launch
    ```

### Step-by-Step Video Guide

For a visual walkthrough of these steps, you can refer to our step-by-step video guide [here]([link-to-video-guide](https://drive.google.com/file/d/1K-UFx4TisEr1YefFvB_rFPcsRqiDuOqY/view?usp=sharing)https://drive.google.com/file/d/1K-UFx4TisEr1YefFvB_rFPcsRqiDuOqY/view?usp=sharing).
