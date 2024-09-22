from flask import Flask, request, jsonify
import base64
import os

app = Flask(__name__)

# POST method
@app.route('/bfhl', methods=['POST'])
def handle_post():
    try:
        data = request.json['data']
        file_b64 = request.json.get('file_b64', None)
        user_id = "john_doe_17091999"
        email = "john@xyz.com"
        roll_number = "ABCD123"
        
        # Separate numbers and alphabets
        numbers = [item for item in data if item.isdigit()]
        alphabets = [item for item in data if item.isalpha()]
        
        # Find the highest lowercase alphabet
        lowercase_alphabets = [char for char in alphabets if char.islower()]
        highest_lowercase = max(lowercase_alphabets) if lowercase_alphabets else []
        
        # File handling (mocked for simplicity)
        if file_b64:
            file_data = base64.b64decode(file_b64)
            file_size_kb = len(file_data) / 1024
            file_valid = True
            file_mime_type = "application/octet-stream"  # Example MIME type
        else:
            file_valid = False
            file_size_kb = 0
            file_mime_type = None

        # Build response
        response = {
            "is_success": True,
            "user_id": user_id,
            "email": email,
            "roll_number": roll_number,
            "numbers": numbers,
            "alphabets": alphabets,
            "highest_lowercase_alphabet": [highest_lowercase],
            "file_valid": file_valid,
            "file_mime_type": file_mime_type,
            "file_size_kb": file_size_kb
        }
        return jsonify(response)
    
    except Exception as e:
        return jsonify({"is_success": False, "error": str(e)}), 400

# GET method
@app.route('/bfhl', methods=['GET'])
def handle_get():
    return jsonify({"operation_code": 1})

if __name__ == "__main__":
    app.run(debug=True)
