
# 🔊 Text-to-Speech Button - Reusable Code

A lightweight, accessible, and easy-to-integrate Text-to-Speech (TTS) button for web applications. Presented at the **AIDL 2026 Symposium** (Accessible and Inclusive Digital Library).

![TTS Button Demo](https://img.shields.io/badge/Accessibility-WCAG%202.1-blue)
![License](https://img.shields.io/badge/license-MIT-green)

## 📖 Overview

This project provides a simple, reusable Text-to-Speech button implementation that can be easily added to any website. The button uses the Web Speech API to read aloud selected text or page content, making your web content more accessible to users with visual impairments or reading difficulties.

## ✨ Features

- 🎯 **One-Click Integration** - Simple copy-paste implementation
- 🎨 **Beautiful UI** - Modern, gradient-styled floating button
- ♿ **WCAG Compliant** - Built with accessibility in mind
- 📱 **Responsive Design** - Works seamlessly on all devices
- 🌐 **Browser Compatible** - Uses the Web Speech API (supported in modern browsers)
- 🎭 **Visual Feedback** - Active state with pulsing animation
- 🔄 **Stop/Start Control** - Pause speech with a second click
- 🎙️ **Smart Selection** - Reads selected text or entire page content

## 🚀 Quick Start

### Option 1: View the Demo

Simply open `index.html` in your browser to see the full demo and documentation.

### Option 2: Integrate into Your Project

Copy the following code snippets into your HTML file:

#### 1. Add the HTML Button

```html
<button class="speaker-button" onclick="toggleSpeech()" aria-label="Toggle Text to Speech">
  <i class="fa fa-volume-up"></i>
</button>
```

#### 2. Add the CSS Styles

```css
.speaker-button {
  position: fixed;
  top: 80px;
  right: 20px;
  width: 50px;
  height: 50px;
  background: linear-gradient(135deg, #4FE0F9 0%, #1a73e8 100%);
  border: none;
  border-radius: 50%;
  color: white;
  font-size: 24px;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(31, 115, 232, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.3s ease;
  z-index: 990;
  padding: 0;
}

.speaker-button:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(31, 115, 232, 0.6);
}

.speaker-button:active {
  transform: scale(0.95);
}

.speaker-button.active {
  background: linear-gradient(135deg, #ff6b6b 0%, #ee5a6f 100%);
  box-shadow: 0 0 20px rgba(255, 107, 107, 0.8);
  animation: pulse-glow 1.5s infinite;
}

@keyframes pulse-glow {
  0%, 100% {
    box-shadow: 0 0 20px rgba(255, 107, 107, 0.8);
  }
  50% {
    box-shadow: 0 0 30px rgba(255, 107, 107, 1);
  }
}
```

#### 3. Add the JavaScript Functionality

```javascript
let isSpeaking = false;
let speechSynthesis = window.speechSynthesis;

function toggleSpeech() {
  const button = document.querySelector('.speaker-button');
  
  if (isSpeaking) {
    speechSynthesis.cancel();
    isSpeaking = false;
    button.classList.remove('active');
    return;
  }

  const selectedText = window.getSelection().toString();
  const textToRead = selectedText || document.body.innerText;
  
  const utterance = new SpeechSynthesisUtterance(textToRead);
  utterance.rate = 1.0;
  utterance.pitch = 1.0;
  utterance.volume = 1.0;
  
  utterance.onstart = () => {
    isSpeaking = true;
    button.classList.add('active');
  };
  
  utterance.onend = () => {
    isSpeaking = false;
    button.classList.remove('active');
  };
  
  utterance.onerror = () => {
    isSpeaking = false;
    button.classList.remove('active');
    alert('Speech synthesis error. Please try again or check browser compatibility.');
  };
  
  speechSynthesis.speak(utterance);
}
```

#### 4. Include Font Awesome (for the icon)

```html
<link href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
```

## 🎯 Usage

1. **Default Behavior**: Click the button to read the entire page content
2. **Reading Selection**: Highlight any text on the page, then click the button to read only that text
3. **Stop Reading**: Click the button again while it's active (red/pulsing) to stop

## 🌐 Browser Compatibility

The Web Speech API is supported in:
- ✅ Chrome/Edge (v33+)
- ✅ Safari (14.1+)
- ✅ Firefox (49+)
- ⚠️ Limited support in older browsers

## 📋 Requirements

- Modern web browser with Web Speech API support
- Internet connection (for Font Awesome icons)
- No additional dependencies required!

## 🎓 Educational Use

This code was developed for the **AIDL 2026 Symposium** to demonstrate practical web accessibility implementation. Feel free to use it for:
- Educational projects
- Personal websites
- Commercial applications
- Accessibility workshops
- Web development training

## 🤝 Contributing

Contributions are welcome! If you have suggestions for improvements:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

You are free to use, modify, and distribute this code for any purpose with attribution.

## 👤 Author

**Arshad Abdul**

Presented at AIDL 2026 Symposium - Accessible and Inclusive Digital Library

## 🙏 Acknowledgments

- AIDL 2026 Symposium for promoting digital accessibility
- Web Speech API for enabling text-to-speech functionality
- The web accessibility community for continuous inspiration

## 📧 Contact

If you have questions, suggestions, or want to discuss accessibility features, feel free to open an issue or reach out!

---

**Made with ❤️ for a more accessible web**

