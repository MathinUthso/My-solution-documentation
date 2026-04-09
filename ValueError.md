<h1> Value error when running uvicorn server</h1>

<h4>uvicorn main:app --reload --port 8000</h4>
<p>If you are trying to run a ROS 2 node (which has its own executor/loop)
  and a Web Server (like FastAPI) in the same script, one of them is likely 
  being pushed to a background thread.</p>
<h6>Solution</h6>
<h5>uvicorn main:app --host 0.0.0.0 --port 8000 --no-install-signal-handlers</h5>
