import time

from flask import Flask, jsonify, render_template, request

app = flask(__name__)

@app.route("/")
def index():
  return render_template("index.html")
  
  @app.route("/posts", methods=["POST"])
  def posts():
  
  #Get start and end point for posts to generate
  start = int(request.form.get("start") or 0)
  end = int(request.form.get("end") or (start + 9))
  
  #Generate list of posts
  data = []
  for i in range(start, end +1):
    data.append(f"Post #{i}")
    
  #Return list of posts
  return jsonify(data)
