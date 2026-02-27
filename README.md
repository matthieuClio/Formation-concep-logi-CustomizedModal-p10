# CustomizedModal – Reusable accessible modal component (JavaScript)

## Project context
This project was developed as part of the **Application Designer & Developer (React-oriented)** training program by OpenClassrooms.  
It's a projet JavaScript curriculum and focuses on building a customizable and accessible modal component that can be integrated into a web interface.

The goal was to create a modal component that:
- Is reusable across multiple interfaces
- Handles focus management
- Supports keyboard accessibility
- Can be controlled programmatically

## Educational objectives
- Build an interactive UI component in vanilla JavaScript
- Manage focus and accessibility (ARIA attributes, tab order, keyboard navigation)
- Create modular, reusable code
- Handle events and state in a component
- Structure code for maintainability and clarity

## Technologies used
- JavaScript (ES6+)
- HTML5
- CSS3
- DOM manipulation
- Accessibility (ARIA)
- Event handling
- Git / GitHub

## Features
- Custom modal component
- Open/close logic with animation support
- Keyboard accessibility (Escape to close, focus trap)
- Reusable API (parameters and configuration)
- Accessible markup with ARIA roles

## Installation and used
This is a simple modal component who can be customized.
(A style css is already apply on the component but you can customized the text notification and the button text)

Quick start :  
1 - If you want to use the library package, you need to install it with the npm command :  
npm i @makabay/customizedmodal

Otherwise clone the project on github
```bash
git clone https://github.com/matthieuClio/Formation-concep-logi-CustomizedModal-p10.git
```
2 - Import the component : 
```js 
// On a Npm library package use case
import { CustomizedModal } from '@makabay/customizedmodal'

// On github clone use case (from ./example/App.tsx)
import CustomizedModal from '../lib/components/CustomizedModal';

```
3 - Define a state who will be shared with the component initialize with boolean (false).
```js 
const [modal, setModal] = useState(false);
```

4 - Define the props component value
```js
const closeButtonTextData = {
    closeButtonTextValue: 'Close',
    textNotificationValue: 'Notification message',
    confirmationTextValue: 'Understood'
};
```

5 - Define the component with his props :
```js
Example :
<CustomizedModal
    closeButtonText={closeButtonTextData.closeButtonTextValue} 
    textNotification={closeButtonTextData.textNotificationValue} 
    confirmationText={closeButtonTextData.confirmationTextValue} 
    modalState={modal}
    changeModalState={setModal}
/>
```

---

I will show you an example of use case comented.

```js
// We will need to share the parent state to our "CustomizedModal" component
import { useState } from "react";

// Components
// On a Npm library package use case
// import { CustomizedModal } from '@makabay/customizedmodal'

// On github clone use case (from ./example/App.tsx)
import CustomizedModal from '../lib/components/CustomizedModal';

// You can replace this App component by the component where you want placed the modal
export default function App () {
    // Here we defined a booleen state hook
    const [modal, setModal] = useState(false);

    // This is the function who will open the modal
    function change () {
        setModal(!modal);
    }

    // This is for CustomizedModal (props) component, it will be your custom text button or message
    const closeButtonTextData = {
        closeButtonTextValue: 'Close',
        textNotificationValue: 'Notification message',
        confirmationTextValue: 'Understood'
    };

    return (
        <>
            {/* A button (example) who will serve of trigger for open modal */}
            <button onClick={change}>
                Open modal {modal} {/* This is just for see the modal state */}
            </button>

            {/* 
            - This is the component -
            He's in absolute position, it's better if it placed in top of the other components on the page
            */}

            {/* 
            - Explaination of the props component -
            closeButtonText={} : will be the text on the close button - string/number
            textNotification={} : will be the modal text message - string/number
            confirmationText={} : will be the text on the confirm button - string/number
            modalState={} : will be the state shared between your component (parent) and the CustomizedModal component (children) - hook (useState) the state initialize with boolean
            changeModalState={} : will be the state method serve to change the state value - hook (useState) the setState function
            */}
            <CustomizedModal
                closeButtonText={closeButtonTextData.closeButtonTextValue} 
                textNotification={closeButtonTextData.textNotificationValue} 
                confirmationText={closeButtonTextData.confirmationTextValue} 
                modalState={modal}
                changeModalState={setModal}
            />
        </>
    );
}
```

## Architecture
.  
├── index.html  
├── css/  
│   └── style.css  
├── js/  
│   ├── modal.js  
│   └── app.js  
├── images/  
└── README.md  

- HTML: markup and modal placeholders
- CSS: styling and transitions
- JavaScript: modal logic and event control

## Areas for improvement
- Add unit tests for open/close and focus logic
- Expand configuration options (callbacks, hooks)
- Add animation controls
- Improve documentation with examples
- Convert to ES modules for reusability

## Author
Project by Matthieu Clio  
Full stack JavaScript web developer
