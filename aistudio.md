https://aistudio.google.com/apps <br/><br/>

Get the image to generate front-end code
<img width="2018" height="2410" alt="image" src="https://github.com/user-attachments/assets/f6a484d7-c11b-4836-8ed9-56941bd42012" />

Upload above image and provide the prompt
<img width="3646" height="981" alt="image" src="https://github.com/user-attachments/assets/9d877a22-02ab-4a2c-a147-c584355aec36" />

Your complete code is generated within couple of minutes
<img width="3580" height="1492" alt="image" src="https://github.com/user-attachments/assets/da17f542-1634-4618-9b09-20342c7c3c85" />

Complete Code

```HTML
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Contact Us</title>
    <script src="https://cdn.tailwindcss.com"></script>
  <script type="importmap">
{
  "imports": {
    "react": "https://esm.sh/react@^19.1.1",
    "react-dom/": "https://esm.sh/react-dom@^19.1.1/",
    "react/": "https://esm.sh/react@^19.1.1/"
  }
}
</script>
</head>
  <body class="bg-white">
    <div id="root"></div>
    <script type="module" src="/index.tsx"></script>
  </body>
</html>
```
Index.tsx
```jsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
const rootElement = document.getElementById('root');
if (!rootElement) {
  throw new Error("Could not find root element to mount to");
}
const root = ReactDOM.createRoot(rootElement);
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```
App.tsx
```jsx
import React, { useState } from 'react';
import FormField from './components/FormField';
const App: React.FC = () => {
  const [formData, setFormData] = useState({
    firstName: '',
    lastName: '',
    email: '',
    phoneNumber: '',
    query: '',
  });
  const [isSubmitting, setIsSubmitting] = useState(false);
  const [statusMessage, setStatusMessage] = useState('');
  const handleChange = (e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement>) => {
    const { id, value } = e.target;
    setFormData(prev => ({ ...prev, [id]: value }));
  };
  const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    setIsSubmitting(true);
    setStatusMessage('');
    // NOTE: This uses the user's default email client.
    // Replace 'contact@example.com' with the actual destination email address.
    const recipientEmail = 'contact@example.com';
    const subject = encodeURIComponent(`New Inquiry from ${formData.firstName} ${formData.lastName}`);
    const body = encodeURIComponent(
      `You have a new contact form submission:\n
First Name: ${formData.firstName}
Last Name: ${formData.lastName}
Email: ${formData.email}
Phone Number: ${formData.phoneNumber}
Message:
${formData.query}`
    );
    const mailtoLink = `mailto:${recipientEmail}?subject=${subject}&body=${body}`;
    // A small delay to give feedback to the user
    setTimeout(() => {
      try {
        window.location.href = mailtoLink;
        setStatusMessage("Success! Your email client should now be open.");
        
        // Reset form
        setFormData({
          firstName: '',
          lastName: '',
          email: '',
          phoneNumber: '',
          query: '',
        });
        
        // Clear message after a while
        setTimeout(() => setStatusMessage(''), 5000);
      } catch (error) {
        console.error("Failed to open mailto link:", error);
        setStatusMessage("Could not open email client. Please copy details manually.");
      } finally {
        setIsSubmitting(false);
      }
    }, 1000);
  };
  return (
    <div className="min-h-screen bg-white flex items-center justify-center py-12 px-4 sm:px-6 lg:px-8">
      <div className="max-w-md w-full">
        <form onSubmit={handleSubmit} className="space-y-2">
          <FormField
            id="firstName"
            label="First Name"
            placeholder="Please enter first name..."
            value={formData.firstName}
            onChange={handleChange}
            required
          />
          <FormField
            id="lastName"
            label="Last Name"
            placeholder="Please enter last name..."
            value={formData.lastName}
            onChange={handleChange}
            required
          />
          <FormField
            id="email"
            label="Email"
            type="email"
            placeholder="Please enter email..."
            value={formData.email}
            onChange={handleChange}
            required
          />
          <FormField
            id="phoneNumber"
            label="Phone Number"
            type="tel"
            placeholder="Please enter phone number..."
            value={formData.phoneNumber}
            onChange={handleChange}
          />
          <FormField
            id="query"
            label="What do you have in mind"
            as="textarea"
            placeholder="Please enter query..."
            value={formData.query}
            onChange={handleChange}
            required
          />
          <div className="pt-4">
            <button
              type="submit"
              disabled={isSubmitting}
              className="w-full flex justify-center py-3 px-4 border border-transparent text-base font-medium rounded-md text-white bg-blue-500 hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500 transition-colors duration-300 disabled:bg-blue-300 disabled:cursor-not-allowed"
            >
              {isSubmitting ? 'Submitting...' : 'Submit'}
            </button>
          </div>
          {statusMessage && (
            <p className={`mt-4 text-center text-sm font-medium ${statusMessage.includes('Success') ? 'text-green-600' : 'text-red-600'}`}>
              {statusMessage}
            </p>
          )}
        </form>
      </div>
    </div>
  );
};
export default App;
```
FormField.tsx

```jsx
import React from 'react';
interface FormFieldProps {
  id: string;
  label: string;
  placeholder: string;
  value: string;
  onChange: (e: React.ChangeEvent<HTMLInputElement | HTMLTextAreaElement>) => void;
  type?: 'text' | 'email' | 'tel';
  as?: 'input' | 'textarea';
  required?: boolean;
}
const FormField: React.FC<FormFieldProps> = ({
  id,
  label,
  placeholder,
  value,
  onChange,
  type = 'text',
  as = 'input',
  required = false,
}) => {
  const commonProps = {
    id,
    name: id,
    placeholder,
    value,
    onChange,
    required,
    className: 'w-full px-3 py-2 bg-white border border-gray-300 rounded-sm focus:outline-none focus:ring-1 focus:ring-blue-500 focus:border-blue-500 placeholder-gray-400 text-gray-900',
  };
  const InputComponent = as === 'textarea' ? 'textarea' : 'input';
  return (
    <div className="mb-4">
      <label htmlFor={id} className="block text-xs font-medium text-gray-600 uppercase tracking-wide mb-2">
        {label}
      </label>
      <InputComponent
        {...commonProps}
        {...(as === 'input' && { type })}
        {...(as === 'textarea' && { rows: 6 })}
      />
    </div>
  );
};
export default FormField;
```
