<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YAY! It's BOGO</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }
        
        body {
            max-width: 500px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f8f8f8;
        }
        
        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            text-align: center;
        }
        
        .product-card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        .pricing-options {
            display: flex;
            gap: 10px;
            margin: 20px 0;
        }
        
        .option {
            flex: 1;
            border: 1px solid #ddd;
            border-radius: 8px;
            padding: 12px;
            cursor: pointer;
            position: relative;
        }
        
        .option.selected {
            border-color: #4CAF50;
            background-color: #f0f8f0;
        }
        
        .popular-tag {
            position: absolute;
            top: -10px;
            right: -5px;
            background: #FF5722;
            color: white;
            padding: 3px 8px;
            border-radius: 10px;
            font-size: 12px;
            font-weight: bold;
        }
        
        .option-title {
            font-weight: bold;
            margin-bottom: 5px;
        }
        
        .discount {
            color: #4CAF50;
            font-size: 14px;
            margin-bottom: 5px;
        }
        
        .current-price {
            font-weight: bold;
            color: #333;
        }
        
        .original-price {
            text-decoration: line-through;
            color: #999;
            font-size: 12px;
        }
        
        .size-options {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin: 15px 0;
        }
        
        .size-option {
            padding: 8px 12px;
            border: 1px solid #ddd;
            border-radius: 20px;
            cursor: pointer;
            font-size: 14px;
        }
        
        .size-option.selected {
            background-color: #4CAF50;
            color: white;
            border-color: #4CAF50;
        }
        
        .delivery {
            color: #4CAF50;
            margin: 15px 0;
            font-weight: bold;
        }
        
        .total {
            font-size: 18px;
            font-weight: bold;
            margin: 15px 0;
            text-align: right;
        }
        
        .add-to-cart {
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 12px;
            border-radius: 5px;
            width: 100%;
            font-size: 16px;
            font-weight: bold;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 5px;
        }
        
        .powered-by {
            text-align: center;
            margin-top: 10px;
            color: #888;
            font-size: 12px;
        }
    </style>
</head>
<body>
    <h1>YAY! It's BOGO</h1>
    
    <div class="product-card">
        <div class="pricing-options">
            <div class="option" onclick="selectOption(this, 10, 24, '10% Off')">
                <div class="option-title">1 Unit</div>
                <div>Standard Price</div>
                <div class="discount">10% Off</div>
                <div class="current-price">$10.00 USD</div>
                <div class="original-price">$24.00 USD</div>
            </div>
            
            <div class="option selected" onclick="selectOption(this, 18, 24, '')">
                <div class="popular-tag">MOST POPULAR</div>
                <div class="option-title">2 Unit</div>
                <div class="current-price">$18.00 USD</div>
                <div class="original-price">$24.00 USD</div>
            </div>
            
            <div class="option" onclick="selectOption(this, 24, 24, '30% Off')">
                <div class="option-title">3 Unit</div>
                <div class="discount">30% Off</div>
                <div class="current-price">$24.00 USD</div>
                <div class="original-price">$24.00 USD</div>
            </div>
        </div>
        
        <div class="option-title">Size</div>
        <div class="size-options">
            <div class="size-option selected" onclick="selectSize(this)">#1</div>
            <div class="size-option" onclick="selectSize(this)">#2</div>
            <div class="size-option" onclick="selectSize(this)">S</div>
            <div class="size-option" onclick="selectSize(this)">Cobur</div>
            <div class="size-option" onclick="selectSize(this)">Black</div>
            <div class="size-option" onclick="selectSize(this)">Cobur</div>
        </div>
        
        <div class="delivery">Free Delivery</div>
        <div class="total">Total : $18.00 USD</div>
        <button class="add-to-cart" onclick="addToCart()">
            + Add to Cart
        </button>
        <div class="powered-by">@ Powered by Pumper</div>
    </div>

    <script>
        let currentPrice = 18;
        let originalPrice = 24;
        
        function selectOption(element, price, original, discount) {
            // Remove selected class from all options
            document.querySelectorAll('.pricing-options .option').forEach(opt => {
                opt.classList.remove('selected');
            });
            
            // Add selected class to clicked option
            element.classList.add('selected');
            
            // Update prices
            currentPrice = price;
            originalPrice = original;
            
            // Update discount display if exists
            const discountEl = element.querySelector('.discount');
            if (discountEl) {
                discountEl.textContent = discount;
                discountEl.style.display = discount ? 'block' : 'none';
            }
            
            updateTotal();
        }
        
        function selectSize(element) {
            // Remove selected class from all sizes
            document.querySelectorAll('.size-options .size-option').forEach(size => {
                size.classList.remove('selected');
            });
            
            // Add selected class to clicked size
            element.classList.add('selected');
        }
        
        function updateTotal() {
            document.querySelector('.total').textContent = `Total : $${currentPrice.toFixed(2)} USD`;
        }
        
        function addToCart() {
            const selectedSize = document.querySelector('.size-option.selected').textContent;
            alert(`Added to cart: ${selectedSize} size for $${currentPrice.toFixed(2)} (Original: $${originalPrice.toFixed(2)})`);
        }
    </script>
</body>
</html>
