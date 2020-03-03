from flask import Flask, make_response, jsonify
from flask_sqlalchemy import SQLAlchemy

application = Flask(__name__)

application.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///database.db'

db = SQLAlchemy(application)
students = db.Table('students', db.metadata, autoload=True, autoload_with=db.engine)


@application.route('/')
def index():
    result = db.session.query(students).all()
    data = []
    for r in result:
        d= {
            'name': r[0],
            'address': r[1],
            'city': r[2],
            'pin code': r[3]
        }
        data.append(d)
    return make_response(jsonify({'data': data}))


if __name__ == '__main__':
    application.run(host='localhost', port=5000, debug=True)
