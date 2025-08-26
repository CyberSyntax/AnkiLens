# AnkiLens

A heads-up display Anki review application for Brilliant Halo smart glasses, enabling hands-free spaced repetition learning through gesture-based interactions.

## 🎯 Overview

AnkiLens transforms your Brilliant Halo smart glasses into a powerful learning tool by seamlessly integrating with AnkiDroid's proven spaced repetition system. Review your flashcards hands-free using simple tap gestures while maintaining focus on your environment.

## ✨ Features

- **Hands-free Review**: Study Anki cards directly on your smart glasses
- **Simple Gestures**: Intuitive tap controls for card ratings
- **Real-time Sync**: Direct integration with AnkiDroid's database
- **Optional Controller**: 8bitdo controller support for advanced features
- **Lightweight Design**: Thin client architecture for optimal battery life
- **Event-driven Communication**: Robust BT LE messaging via frame_msg SDK

## 🏗 Architecture

```
[Halo: Lua Event Loop] <-> [frame_msg SDK] <-> [BT LE] <-> [Flutter App] -> [Platform Channels] -> [AnkiDroid ContentProvider]
```

### Components

- **Flutter Host App**: The brain - manages state, logic, and orchestrates communication
- **Brilliant Halo**: The interface - renders UI and captures user input
- **AnkiDroid ContentProvider**: The data source - official API for card operations
- **frame_msg SDK**: The messenger - handles robust device communication

## 📋 Requirements

### Hardware
- Brilliant Halo smart glasses
- Android smartphone (Android 5.0+)
- Optional: 8bitdo controller for extended features

### Software
- AnkiDroid installed and configured with decks
- Flutter SDK (3.0+)
- Android Studio or VS Code with Flutter extensions
- Brilliant Halo SDK and tools

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/CyberSyntax/AnkiLens.git
cd AnkiLens
```

### 2. Set Up Flutter App
```bash
cd flutter_app
flutter pub get
```

### 3. Configure AnkiDroid Integration
Ensure AnkiDroid is installed and has the ContentProvider API enabled:
- Install AnkiDroid from Google Play Store
- Enable "Advanced" > "Enable API" in AnkiDroid settings
- Grant necessary permissions when prompted

### 4. Deploy Lua Script to Halo
```bash
# Use Brilliant's deployment tool
cd halo_lua
# Follow Brilliant Halo documentation for deployment
```

### 5. Build and Run
```bash
flutter run
```

## 🎮 Controls

### On-Glass Gestures

| Gesture | Action | Description |
|--------------------------------|----------|----------------------------------|
| Single Tap | Show Answer | Reveals the answer on the card |
| Single Tap (after answer shown) | Good (3) | Card was recalled correctly |
| Double Tap | Again (1) | Card needs more review |
| Long Press | Undo | Revert last review action |
| Triple Tap | Bury Card | Hide card from current session |

### 8bitdo Controller (Optional)

| Button | Action | Description |
|--------|--------|-------------|
| Up | Adjust Flag | If flag=0: set to 4. If flag>1: decrease by 1 (higher priority). If flag=1: stays at 1 |
| Down | Adjust Flag | If flag=0: set to 4. If flag<7: increase by 1 (lower priority). If flag=7: stays at 7 |

## 📱 Usage

1. **Start AnkiDroid**: Ensure AnkiDroid is running in the background
2. **Launch AnkiLens**: Open the Flutter app on your phone
3. **Connect Halo**: The app will automatically connect to your glasses
4. **Start Reviewing**: Cards will appear on your glasses display
5. **Rate Cards**: Use tap gestures to rate each card
6. **Automatic Progression**: Next card loads automatically after rating

## 🔄 Review Workflow

1. Card appears on Halo display
2. User reviews and recalls answer
3. User taps to rate difficulty
4. Rating sent to AnkiDroid
5. AnkiDroid updates scheduling
6. Next card automatically displayed

## 🛠 Development

### Project Structure
```
ankilens/
├── flutter_app/           # Flutter host application
│   ├── lib/
│   │   ├── services/     # Core services
│   │   ├── models/       # Data models
│   │   └── platform_channels/  # Android integration
│   └── android/          # Platform-specific code
├── halo_lua/            # Brilliant Halo scripts
│   └── anki_review_loop.lua
└── docs/                # Additional documentation
```

### Building from Source

#### Flutter App
```bash
cd flutter_app
flutter build apk --release
```

#### Lua Scripts
Follow Brilliant Halo SDK documentation for compilation and deployment.

### Testing
```bash
flutter test
```

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **AnkiDroid Team**: For the excellent ContentProvider API and continued development
- **Anki/Damien Elmes**: For creating the original Anki and its AGPL-licensed codebase
- **Brilliant Labs**: For the innovative Halo smart glasses platform
- **frame_msg Contributors**: For the robust messaging SDK

## 📚 Resources

- [AnkiDroid Documentation](https://github.com/ankidroid/Anki-Android/wiki)
- [Brilliant Halo SDK](https://docs.brilliant.xyz/)
- [Flutter Documentation](https://flutter.dev/docs)
- [Anki Manual](https://docs.ankiweb.net/)

## 🐛 Known Issues

- Battery life varies based on review frequency
- Some special card types have limited support

## 📮 Support

- **Issues**: [GitHub Issues](https://github.com/CyberSyntax/AnkiLens/issues)
- **Wiki**: [Project Wiki](https://github.com/CyberSyntax/AnkiLens/wiki)

## 🗺 Roadmap

- [ ] Voice command support
- [ ] Multiple deck selection
- [ ] Statistics overlay
- [ ] Custom gesture mapping

---

**Made with ❤️ for the spaced repetition learning community**
