# Software that should be downloaded already by this step
* Unreal downloaded here: https://www.unrealengine.com/en-US/get-now/agnostic
* Live Link Face app for iOS (Requires iOS 13.0 or later). Compatable with iPhone, iPad, and iPod touch. 


# Download Our Repo

**3. Importing into Unreal**
   - You should have our project downloaded or cloned on your computer by this point.
   - Once the project is downloaded make sure you save it a place where you can find it easily. Please refer to Unreal’s documentation on setting up the Unreal environment and selecting the map for prototyping. Here is the link again https://docs.unrealengine.com/en-US/Platforms/AR/HandheldAR/FaceARSample/index.html. 

      - When you open the faceAR project in Unreal again, import the FBX into Unreal with these settings:

![import screenshot](https://i.ibb.co/LnhVCvm/Screen-Shot-2020-02-10-at-5-05-25-PM.png)



  - Need to make sure that “Import Morph Targets”  is checked off. Once it is imported as a mesh and as skeletal, the import default settings should take care of itself. 

If you need further assistance, refer to this documentation from Unreal: https://docs.unrealengine.com/en-US/Engine/Content/FBX/MorphTargets/index.html

Once it is imported into Unreal. You should be able to open up the skeletal mesh asset and see the renamed blendshapes. Test the sliders to see if they work on the model. 

### Reallusion example

![reallusion](Media/reallusion6.png)


If you see an error or the blendshapes are named differently, make sure to double check the grouping name of the blendshapes, this is the group that should be named “Blendshape_mesh”. 

![Maya screenshot](https://i.ibb.co/D9QDx1n/Annotation-2020-02-27-110918.png)

In this example, the “Body_ncl1_4” needs to be renamed to Blendshape_mesh. 

Our repo will have everything set up for you to test the Livelink app on yor phone with our Unreal sample project.

## Adding eye movements

  **How to make eyes move** (try this out on our sample reallusion model). 
  1. Create a new PoseAsset (Create Asset - Create PoseAsset - Current Pose)
        - ![1](https://i.ibb.co/nC3VtpV/1.png)
  2.  In the PoseAsset, add eye movements. 
        - a. **To do this:**
           - **Rotate the eyeball to the position you want the pose to be.**
	       - ![2](https://i.ibb.co/hLd9ZQD/2.png)
	    - b. **Insert Pose to the PoseAsset (Create Asset - Create PoseAsset - Insert Pose - [Choose Your PoseAsset]).**
	       - ![3](https://i.ibb.co/KzZrPSV/3.png)
	    - c. **Slide the slidebar of the new pose to 1. The eyeball will now be in an unwanted position, but it’s okay.**
	       - ![4](https://i.ibb.co/QFWsgKp/4.png)
	    - d. **Rotate the eyeball back to where you want it to be.**
	       - ![5](https://i.ibb.co/WvmV6jk/5.png)
	    - e. **Slide the slidebar of the new pose back to 0.**
	       - ![6](https://i.ibb.co/PQd3XwJ/6.png)  
	    - f. **Rename the new pose according to the naming conventions for Apple blendshapes (https://developer.apple.com/documentation/arkit/arfaceanchor/blendshapelocation)**
	       - ![7](https://i.ibb.co/PgFSYnK/7.png)
	    - g. **Do the above for all other poses, the result should look like this:**
	       - ![8](https://i.ibb.co/hXYWv9d/8.png) 
		   - Note: You should rotate the eyeball to the position you want first, and then insert a new pose. You can delete Pose_0 in the screenshot above.
	    - h. **Connect the PoseAsset in Animation Blueprint. It should work now.**
		   - ![9](https://i.ibb.co/KLvTM25/9.png)

		
## Enabled plugins in Unreal 

   - Make sure these plugins are enabled in Unreal. 
     - **Livelink** 
     - ![plugins](https://i.ibb.co/j8J5xKY/Rlab-facetracking2-Unreal-Editor-6-29-2020-3-00-28-PM.png)
   - **Apple ARkit**
     - ![Appleplugins](https://i.ibb.co/N1KPM8W/Rlab-facetracking2-Unreal-Editor-6-29-2020-3-00-37-PM-2.png)

   - **LiveLink**
     - Make sure you are able to see your phone
     - ![Livelink](https://i.ibb.co/02n2Xvq/Rlab-facetracking2-Unreal-Editor-6-29-2020-3-19-35-PM-2.png)


## Blueprints in Unreal

- Check out our blueprints that should be set up for you already. Make sure our level blue print has a *Start-AR-Session* node connected to *Event Begin Play* 
- You should see two sample characters in the project. Go into their animation blueprints and see how they are set up. 

- We have already prepared the sample blueprints for you in this project.

**Use the Unreal documentation for a more detailed set up.**

Steps for getting the iPhone to control facial movements in Unreal. 
Please refer to the documentation from Unreal to setup the face tracking from scratch here:
https://docs.unrealengine.com/en-US/Platforms/AR/HandheldAR/FaceARSample/index.html

Here is a link to Apple’s blendshape guidelines: https://developer.apple.com/documentation/arkit/arfaceanchor/blendshapelocation

   - **Here is a simplified list of the setup:**
     - Make sure the blendshapes are named correctly. 
     - Enable face tracking in the Defaultengine.ini file. 
     - Create and apply the data asset.
     - Create a sessionAR function in the level blueprint. 

     - Create an animation blueprint that connects livelink node and set the name to “iPhoneXFaceAR” exactly. 
       - Right click in the content browser in an empty space > go to “Animation” > select “Animation blueprint” > Under parent class Select “anim instance” > Under target skeleton select the name of your imported fbx file > click “ok” and rename it and make sure you know where it is. 

   - **Level Blueprint**
     - ![LevelBlueprint](https://i.ibb.co/Lk6RV6j/RLab-Sample-map-6-29-2020-3-44-14-PM-2.png)
   - **Animation Blueprint**
   - **Example animation blueprint**
      - ![reallusion blueprint](Media/reallusion13.png)



# Download The App

Look on the app store on your iPhone and download the *Live Link Face* app. To Learn more about how to set the connection on your phone go to Unreal's [documentation](https://docs.unrealengine.com/en-US/Engine/Animation/FacialRecordingiPhone/index.html) for further instructions. 

![iphone app](Media/livelink.png)

  - Type in your ip adress
  - To find out what your IPv4 adress is:

On PC: Open the command line and type in
```
ipconfig
```
On Mac type in 
```
ifconfig
```
Or go into your "system preferences" click on "Network" and then you will see the ip address on the right. 


## Almost Done! 

  - Make sure your phone and computer are connected on the same network!
  - On the app click connect and then press play in Unreal, while it's running, you might need to click again on the phone app and you will start to see the faces move!

  **Congratualtions!** You just completed facial tracking in Unreal for free!

  
## If you encountered an error refer back to the previous steps, if you need to! 

## If you need to go back to the table of [contents](https://github.com/RLabNYC/RLab_Facetracking). For the Python scripts steps go [here](https://github.com/RLabNYC/Rlab_FaceTracking_reallusion/blob/master/RUNSCRIPT.md)

## Editing the blendshapes more in maya
If you feel that the facial expressions can be exaggerated more you can look into more maya techniques in manipulating the mesh [here](https://youtu.be/iTPxiQVMlbE?t=737).
You can refer to this tutorial on editing blendshaps with the verticies [here](https://www.youtube.com/watch?v=C29DJYBLh_M&t=155s). 
### Example of editing the mesh
![mesh edit](Media/mesh.gif)


# Conclusion

There are a lot more other 3D software to create your avatars with out there. Some have a trial subcription others have: 

[Daz3D](https://www.daz3d.com/get_studio/)
 - Daz has a lot of lot of assets use in their studio and it can export to Blender, Maya, 3ds max, and Cinema4D 

## Next steps for you
 - Some areas to build off from this tutorial would be to more textures and material to your character.
 - Adding hair and clothing and having it move in real time would be great next steps to dive into. Here is a [link](https://www.youtube.com/watch?v=9FYgoPZAZRA&list=TLPQMDYwODIwMjDv7CDRqBva0w&index=5) on applying hair on a avatar. Here is a [link](https://www.youtube.com/watch?v=9nLz4yTzbtw&t=454s) to create hair in Maya. 
   - Here are some links for more inspiration:
   - Matt Workman has a lot post on [facial tracking](https://www.youtube.com/watch?v=bf07hCA3Co0) and [virtual production](https://www.youtube.com/watch?v=C-M_GEKKmfU&t=21s)

## TODO 
**We are still having trouble getting the facial hair to move with blendshape targets, we would appreciate if someone within the community could help us out on this. Thank you!**



Please feel free to add content by pullrequests, we are three to four people managing this repo, so our review process will be relatively fast. 

  - **Make A Branch**
    - Please create a separate branch for each issue that you're working on. Do not make changes to the default branch (e.g. master, develop) of your fork.
  - **Push Your Code ASAP**
    - Push your code as soon as you can. Follow the ["early and often"](https://www.worklytics.co/blog/commit-early-push-often/) rule.
    - Make a pull request as soon as you can and **mark the title with a "[WIP]"**. You can create a [draft pull request](https://help.github.com/en/articles/about-pull-requests#draft-pull-requests).[Screenshot: How to create draft PR?](https://opensource.creativecommons.org/contributing-code/pr-guidelines/draft_pr.gif). 
  - **Describe Your Pull Request**
    - Use the format specified in pull request template for the repository. Populate the stencil completely for maximum verbosity.
      - Tag the actual issue number by replacing #[issue_number] e.g. #42. This closes the issue when your PR is merged.
      - Tag the actual issue author by replacing @[author] e.g. @issue_author. This brings the reporter of the issue into the conversation.
      - Mark the tasks off your checklist by adding an x in the [ ] e.g. [x]. This checks off the boxes in your to-do list. The more boxes you check, the better.
    - Describe your change in detail. Too much detail is better than too little.
    - Describe how you tested your change.
    - Check the Preview tab to make sure the Markdown is correctly rendered and that all tags and references are linked. If not, go back and edit the Markdown.
    - [Screenshot: Populated pull request](https://opensource.creativecommons.org/contributing-code/pr-guidelines/populated_pr.png).
  - **Request Review**
    - Once your PR is ready, remove the "[WIP]" from the title and/or change it from a draft PR to a regular PR.
    - If a specific reviewer is not assigned automatically, please [request a review](https://help.github.com/en/articles/requesting-a-pull-request-review) from the project maintainer and any other interested parties manually.
  - **Incorporating feedback**
    - If your PR gets a 'Changes requested' review, you will need to address the feedback and update your PR by pushing to the same branch. You don't need to close the PR and open a new one.
    - Be sure to re-request review once you have made changes after a code review.
    - [Screenshot: How to request re-review?](https://opensource.creativecommons.org/contributing-code/pr-guidelines/rereview.png)
    - Asking for a re-review makes it clear that you addressed the changes that were requested and that it's waiting on the maintainers instead of the other way round.
    - [Screenshot: Difference between 'Changes requested' and 'Review required'](https://opensource.creativecommons.org/contributing-code/pr-guidelines/difference.png).
