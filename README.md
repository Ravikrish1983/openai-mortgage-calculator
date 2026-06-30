# Mortgage Pre-Approval Calculator

An interactive, ChatGPT-compatible mortgage pre-approval calculator with a slick inline card design inspired by Rocket Mortgage.

## Features

✨ **Interactive Form**
- Full Name input
- Annual Income field (with $ prefix)
- Monthly Debt Obligations field (with $ prefix)
- Real-time validation with error messages

🎯 **Pre-Approval Estimate Card**
- Personalized greeting with applicant name
- Prequalified loan amount
- Required down payment (20%)
- Interest rate and APR display
- 30-day validity period
- Glassmorphic design with smooth animations

📱 **Responsive Design**
- Mobile-friendly (works on phones, tablets, desktops)
- Touch-optimized inputs
- Smooth animations and transitions

🔒 **Smart Validation**
- Validates all user inputs
- Checks debt-to-income ratio (max 50%)
- Prevents invalid submissions
- Clear error messages

## How It Works

### Mortgage Calculation
The calculator uses industry-standard formulas:

1. **Monthly Income**: Annual Income ÷ 12
2. **Max Monthly Payment**: Lesser of:
   - 28% of monthly gross income, OR
   - 36% of monthly income minus existing monthly debt
3. **Loan Amount**: Calculated using 30-year amortization at market rates
4. **Down Payment**: 20% of total home value
5. **Interest Rate**: 6.1% (configurable)
6. **APR**: 6.58% (configurable)

### Validation Rules
- Name must be at least 2 characters
- Annual income must be > $0
- Monthly debt cannot be negative
- Debt-to-income ratio must not exceed 50%

## Usage

### Standalone
Simply open `index.html` in a web browser.

### OpenAI GPT Integration

#### Option 1: View Online
Open in your browser:
```
https://htmlpreview.github.io/?https://raw.githubusercontent.com/Ravikrish1983/openai-mortgage-calculator/main/index.html
```

#### Option 2: Embed as Iframe
```html
<iframe src="https://raw.githubusercontent.com/Ravikrish1983/openai-mortgage-calculator/main/index.html" 
        width="600" 
        height="800" 
        frameborder="0">
</iframe>
```

#### Option 3: ChatGPT Custom Action
1. Go to ChatGPT Plus → Custom GPT
2. Add Action with this schema:
```json
{
  "openapi": "3.0.0",
  "info": {
    "title": "Mortgage Calculator",
    "version": "1.0.0"
  },
  "servers": [
    {
      "url": "https://raw.githubusercontent.com/Ravikrish1983/openai-mortgage-calculator/main"
    }
  ],
  "paths": {
    "/index.html": {
      "get": {
        "operationId": "getMortgageCalculator",
        "summary": "Get the mortgage pre-approval calculator"
      }
    }
  }
}
```

#### Option 4: Direct GitHub Pages
Enable GitHub Pages in repository settings (Settings → Pages → Source: main branch)

## Customization

### Adjust Interest Rates
Edit lines ~265-266 in `index.html`:
```javascript
const baseRate = 6.1;  // Change this
const apr = 6.58;       // And this
```

### Modify Debt-to-Income Ratio Limits
Edit lines ~252-256:
```javascript
const maxMonthlyPayment = Math.min(
    monthlyIncome * 0.28,  // Frontend ratio
    monthlyIncome * 0.36 - monthlyDebt  // Backend ratio
);
```

### Adjust Down Payment Percentage
Edit lines ~273-274:
```javascript
const totalHomeValue = loanAmount / 0.80;  // This means 20% down
const downPayment = totalHomeValue * 0.20;  // Change to desired %
```

### Change Validity Period
Edit line ~280:
```javascript
expirationDate.setDate(expirationDate.getDate() + 30);  // Change 30 to desired days
```

## Styling

The calculator uses:
- **Colors**: Purple gradient (#667eea → #764ba2)
- **Font**: System fonts (Apple, Segoe UI, Helvetica)
- **Animations**: Smooth CSS transitions and keyframe animations
- **Glassmorphism**: Blur effect on card content

All styles are embedded in `index.html` for easy deployment.

## Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

## Data Privacy

This calculator:
- ✅ Runs entirely in the browser
- ✅ No server calls or API requests
- ✅ No data storage or tracking
- ✅ No third-party services

All calculations are done client-side.

## File Structure

```
openai-mortgage-calculator/
├── index.html          # Complete calculator (single file)
├── README.md          # This file
└── LICENSE            # Optional
```

## Disclaimer

This is a pre-approval **estimate** for educational purposes. It is not a formal loan offer. Actual mortgage approval depends on:
- Credit score and history
- Employment verification
- Income verification
- Property appraisal
- Final underwriting review

## License

Free to use and modify for personal and commercial purposes.

## Support

For issues or feature requests, open an issue in the repository.

---

**Ready to integrate?** Copy the `index.html` file URL and embed it anywhere! 🚀