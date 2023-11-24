# Oral script for the video presentation

## Greetings

Hi guys it's Martin here, I will present you ways to store and visualize your MDAnalysis data.

## Data storage

You may or may not know that there are many file formats in molecular dynamics and hopefully MDAnalysis supports many of them. We provided a link to the official documentation if your want to have a closer.

### How to write data

So imagine, you have a universe containing a trajectory and you want to extract informations of specific frames or even all of them, how can you actually do that ?

The most common way is to write them into a file. This is done by selecting your atoms, and using the `.write()` method that asks you to provide a file name. Note that the extension is very important as it will be automatically detected by MDAnalysis if it is supported. In this example we are saving information the alpha carbons into a file in the PDB format. This is done by default on the current frame but you can decide to extract the information for all the frames by adding the "frame" argument and specifying 'all'. If you want to specific frames, you can access the trajectory of your universe in a python list manner.

## Visualization

### Making plots

So you saved your information but maybe you also want to check the actual behavior of your trajectory and for that a plot might give your an exhaustive answer.

On this example we plotted the radius of gyration of the trajectory. How did we do it ?

We iterate through the trajectories to extract information from each frame into two lists. The time information is contained in the universe trajectory object and the radius of gyration information is extracted with the MDAnalysis `radius_of_gyration()` method. With those lists we create a pandas dataframe and we do a simple plot matplotlib plot. Now this is a plot, it is static and very specific and maybe you just want to visualize in 3D how your trajectory went ? Thats where NGLView comes in.

### NGLView for 3D visualization

So what is it ? It is a interactive widget that allows you to visualize your trajectory directly in your Jupyter Notebook, no need to go on another program, how cool is that ?
You might wonder how it's done so let's get started immediately, it is super easy. 

Now you have prepared your MDAnalysis universe and you are wondering how to visualize it. The answer is simple. Use the NGLView method dedicated to MDAnalysis called `.show_mdanalysis()` and give the name of your universe. A widget is created and can be viewed by invoking it.

You can do many other things if you know of to play with your universe and the NGLWiew parameters. In the following example I will show how to visualize the full trajectory of the tubulin superimosed on it's first frame. 

We first created two copies of the same universe and did a backbone alignment of the trajectory onto the first frame of the trajectory. The resulting aligned trajectory is saved to a new file that will be used to recreate the mobile universe. Then we created a widget for our universe that contains the trajectory. Finally we added a new component to our widget, which is the structure of the first frame by using the `add_component()` method and providing the reference universe. Note that is only adds the first frame and not the full trajectory. For an easier visualization, we changed the color of the cartoon of our different components with the `update_cartoon()` method and specifying the component and the color to update.

If you want to see other parameters to customize your view, your can refer to the API documentation, there is plenty of them.
