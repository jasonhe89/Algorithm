/Users/jianshenhe/guestbook

\>\>\> from guestbook import db

![screenshot.png](resources/EFBAB69D083675C6F9ED004BD95E471A.png)

```python
import datetime
import flask
import os
from flask.ext.sqlalchemy import SQLAlchemy

app = flask.Flask(__name__)      # a Flask object

basedir = os.path.abspath(os.path.dirname(__file__))

app.config['SECRET_KEY'] = 'hard to guess string'
app.config['SQLALCHEMY_DATABASE_URI'] =\
    'sqlite:///' + os.path.join(basedir, 'data.sqlite')
app.config['SQLALCHEMY_COMMIT_ON_TEARDOWN'] = True

db = SQLAlchemy(app)



@app.route('/display_entries')            # called when visiting web URL 127.0.0.1:5000/
def display_entries():
    return flask.render_template('guestbook.html',)
    

@app.route('/add_entry')         # called when visiting web URL 127.0.0.1:5000/bye
def add_entry():
    guestbook_id = flask.request.args.get('guestbook_id')
    name = flask.request.args.get('name')
    comment = flask.request.args.get('comment')
    gb = GuestBook(guestbook_id = guestbook_id, comment = comment, name = name, date = datetime.datetime.now())
    db.session.add(gb)
    db.session.commit()
    return flask.redirect(flask.url_for('display_entries'))
    
    
class GuestBook(db.Model):
    __tablename__ = 'guestbooks'
    id = db.Column(db.Integer, primary_key = True)
    guestbook_id = db.Column(db.Integer)
    comment = db.Column(db.String(1024))
    name = db.Column(db.String(64))
    date = db.Column(db.DateTime)
    
if __name__ == '__main__':
    db.create_all()
    app.run(debug=True, port=5000)


#if __name__ == '__main__':
#    app.run(debug=True, port=5000)    # app starts serving in debug mode on port 5000
    
```