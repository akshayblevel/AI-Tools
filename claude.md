https://claude.ai <br/> <br/>
Get the image to generate HTML & CSS
<img width="2018" height="2410" alt="image" src="https://github.com/user-attachments/assets/ecc10ad4-332a-455d-b3f7-fb610b9bb379" />
Prompt to generate HTML & CSS
<img width="1978" height="711" alt="image" src="https://github.com/user-attachments/assets/a17a061c-d33d-4572-9a6b-504c0ae8d19c" />
HTML & CSS will be generated
<img width="1818" height="2133" alt="image" src="https://github.com/user-attachments/assets/227d49ae-1f1d-48c7-8ff3-0ed6b456d1dc" />
Complete HTML 
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Form</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background-color: #f8f9fa;
            padding: 40px 20px;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .form-container {
            background: white;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            width: 100%;
            max-width: 500px;
        }

        .form-group {
            margin-bottom: 24px;
        }

        .form-group:last-of-type {
            margin-bottom: 32px;
        }

        label {
            display: block;
            margin-bottom: 8px;
            font-size: 14px;
            font-weight: 500;
            color: #6b7280;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        input[type="text"],
        input[type="email"],
        input[type="tel"],
        textarea {
            width: 100%;
            padding: 16px;
            border: 2px solid #e5e7eb;
            border-radius: 8px;
            font-size: 16px;
            color: #374151;
            background-color: #ffffff;
            transition: border-color 0.2s ease;
        }

        input[type="text"]:focus,
        input[type="email"]:focus,
        input[type="tel"]:focus,
        textarea:focus {
            outline: none;
            border-color: #60a5fa;
        }

        input::placeholder,
        textarea::placeholder {
            color: #9ca3af;
            font-size: 16px;
        }

        textarea {
            min-height: 120px;
            resize: vertical;
            font-family: inherit;
        }

        .submit-btn {
            width: 100%;
            padding: 16px;
            background-color: #60a5fa;
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s ease;
        }

        .submit-btn:hover {
            background-color: #3b82f6;
        }

        .submit-btn:active {
            transform: translateY(1px);
        }

        @media (max-width: 640px) {
            .form-container {
                padding: 24px;
                margin: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="form-container">
        <form id="contactForm">
            <div class="form-group">
                <label for="firstName">FIRST NAME</label>
                <input type="text" id="firstName" name="firstName" placeholder="Please enter first name..." required>
            </div>

            <div class="form-group">
                <label for="lastName">LAST NAME</label>
                <input type="text" id="lastName" name="lastName" placeholder="Please enter last name..." required>
            </div>

            <div class="form-group">
                <label for="email">EMAIL</label>
                <input type="email" id="email" name="email" placeholder="Please enter email..." required>
            </div>

            <div class="form-group">
                <label for="phone">PHONE NUMBER</label>
                <input type="tel" id="phone" name="phone" placeholder="Please enter phone number...">
            </div>

            <div class="form-group">
                <label for="message">WHAT DO YOU HAVE IN MIND</label>
                <textarea id="message" name="message" placeholder="Please enter query..." required></textarea>
            </div>

            <button type="submit" class="submit-btn">Submit</button>
        </form>
    </div>

    <script>
        document.getElementById('contactForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Get form data
            const formData = {
                firstName: document.getElementById('firstName').value,
                lastName: document.getElementById('lastName').value,
                email: document.getElementById('email').value,
                phone: document.getElementById('phone').value,
                message: document.getElementById('message').value
            };
            
            // Simple success message (replace with your form handling logic)
            alert('Form submitted successfully!');
            console.log('Form data:', formData);
            
            // Reset form
            this.reset();
        });
    </script>
</body>
</html>
<img width="2436" height="7092" alt="image" src="https://github.com/user-attachments/assets/3c3ef90e-ce61-4159-be30-86e8be83a609" />

```



