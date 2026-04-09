<h1> Value error when running uvicorn server</h1>

<h4>uvicorn main:app --reload --port 8000</h4>
<p>If you are trying to run a ROS 2 node (which has its own executor/loop)
  and a Web Server (like FastAPI) in the same script, one of them is likely 
  being pushed to a background thread.</p>
<h6>Solution</h6>
<h5>Step 1: Eliminate threads</h5>

<p>
  def start_ros():
    ...
    ros_client.run_forever()

threading.Thread(target=start_ros,daemon=True).start()</p>

<h5>Step 2:Remove .forever</h5>
<p>ros_client.run_forever()</p>
<p>threading.Thread(target=start_ros).start()</p>

<h5>Step 3: Add this</h5>
<p>ros_client.connect()</p>
<p>import threading                    ❌
threading.Thread(...).start()      ❌
ros_client.run_forever()           ❌</p>
