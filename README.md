![image](https://github.com/user-attachments/assets/6845fcbe-3a95-47e5-8c1f-1c67247b2676)

# Browser Not Opening 

![image](https://github.com/user-attachments/assets/4f7b972f-d63d-4834-9450-53b140b068d5)

# Currently Terminal not Opening


# 8os

A new way to compute.

## Installation on Arch Linux with i3WM

### Prerequisites

1. Update system packages:
```bash
sudo pacman -Syyu
```

2. Install required dependencies:
```bash
sudo pacman -S nodejs npm python xdg-utils
```

### i3WM Configuration

1. Open your i3 config file:
```bash
nano ~/.config/i3/config
```

2. Add the following rules to allow the application to open external programs:
```bash
# Terminal UI Application Rules
for_window [class="8os"] floating enable
for_window [class="8os"] border pixel 2
```

3. Configure application permissions:
```bash
# Create a policy file
sudo nano /etc/polkit-1/rules.d/50-8os.rules
```

4. Add the following content:
```javascript
polkit.addRule(function(action, subject) {
    if (action.id == "org.freedesktop.policykit.exec" &&
        subject.local &&
        subject.active &&
        subject.isInGroup("wheel")) {
            return polkit.Result.YES;
    }
});
```

5. Add your user to required groups:
```bash
sudo usermod -aG wheel $USER
```

6. Log out and log back in for changes to take effect.

### Installation Steps

1. Clone the repository:
```bash
git clone https://github.com/boodidly/8os.git
cd 8os
```

2. Install project dependencies:
```bash
npm install
```

### Running the Application

1. Start the development server:
```bash
npm run dev
```

2. Open your browser and navigate to:
```
http://localhost:3000
```

## Features

- **Integrated Browser**: Default browser view in the main panel
- **Custom Commands**: Add your own command buttons with the '+' button
- **Theme Customization**: Adjust colors and glow effects
- **Built-in Tools**
  - Node.js REPL
  - NPM Interface
  - JSON Tools
  - Application Importer

## Usage

### Default Buttons
- **Check Mail**: Runs the mail checking script
- **Node.js**: Opens Node.js REPL
- **NPM**: Shows NPM command interface
- **JSON Tools**: Provides access to JQ
- **Import Application**: Import external applications

### Custom Buttons
1. Click the '+' button
2. Enter button name and command
3. Click 'Add Button'

### Opening Applications
- Use the `open` command followed by the application name
- Example: `open firefox`

### Removing Buttons
1. Click the trash icon
2. Select buttons to remove
3. Click again to exit delete mode

### Theme Customization
1. Click the settings icon
2. Adjust colors and effects
3. Changes apply immediately

## Keyboard Shortcuts

- **Double-click**: Toggle fullscreen panel
- **Esc**: Exit fullscreen mode

## System Requirements

- Arch Linux
- i3WM
- Node.js 18+
- NPM 8+
- Python 3.x
- Modern web browser
- xdg-utils

## Troubleshooting

If you encounter permission issues:

1. Check group membership:
```bash
groups $USER
```

2. Verify polkit rules:
```bash
ls -l /etc/polkit-1/rules.d/50-8os.rules
```

3. Restart polkit:
```bash
sudo systemctl restart polkit
```

## License
Free To All Good Homes

I/We Take All Care && Zero, Zip, Zilch Resposibility For Any Harm, Loss, Deconstruction or Appocolyptical Type Outcomes Caused by using our Lovely Software,  Enjoy ;~}  

Don't Forget to Tip on The Way Out, Let's Keep it Free For Those Who Can't afford It !!!
