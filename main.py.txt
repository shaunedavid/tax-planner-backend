from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/calculate', methods=['POST'])
def calculate():
    # Extract input data
    data = request.json
    age = data.get('age')
    income = data.get('income')
    filing_status = data.get('filing_status')
    retirement_balance = data.get('retirement_balance')

    # Example response
    result = {
        "Tax Bracket": "22%",
        "RMD Amount": f"${retirement_balance / 26.5:.2f}",
        "IRA Eligibility": "Eligible for full Roth IRA contribution",
        "Capital Gains Tax Rate": "15%",
        "IRMAA Surcharge": "$0 per month"
    }
    return jsonify(result)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
