```
[Unit]
Description=Flask App
After=network.target

[Service]
User=your_user
Group=your_group
WorkingDirectory=/path/to/your/flask/app
Environment="FLASK_APP=your_flask_app.py"
ExecStart=/usr/bin/python3 /path/to/your/flask/app/your_flask_app.py
Restart=always

[Install]
WantedBy=multi-user.target
```