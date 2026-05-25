# 🏝️ Dynamic Island for Windows

A fluid, highly responsive desktop pill overlay inspired by iPhone's Dynamic Island. Built natively using Windows APIs and hardware-accelerated Direct2D rendering to bring a beautiful, modern, and buttery-smooth 60 FPS notification and media widget directly to your Windows desktop with virtually zero impact on system resources.

---

## 📸 Preview & Showcases

<p align="center">
  <img src="https://raw.githubusercontent.com/devcode90/STONIC-3.0/main/Screenshot%202026-05-25%20201746.png" alt="Dynamic Island Preview 1" width="280" style="border-radius: 8px; margin: 10px;"/>
  <img src="https://raw.githubusercontent.com/devcode90/STONIC-3.0/main/Screenshot%202026-05-25%20201826.png" alt="Dynamic Island Preview 2" width="280" style="border-radius: 8px; margin: 10px;"/>
  <img src="https://raw.githubusercontent.com/devcode90/STONIC-3.0/main/Screenshot%202026-05-25%20201836.png" alt="Dynamic Island Preview 3" width="280" style="border-radius: 8px; margin: 10px;"/>
  <img src="https://raw.githubusercontent.com/devcode90/STONIC-3.0/main/Screenshot%202026-05-25%20201852.png" alt="Dynamic Island Preview 4" width="280" style="border-radius: 8px; margin: 10px;"/>
</p>

---

## ✨ Features

- 🟢 **Hardware Privacy Indicators:** A pulsing orange dot appears when your microphone is active, and a green dot when your camera is in use. Highly optimized polling ensures absolutely zero CPU drain.
- 🎵 **Rich Media Integration:** Displays high-quality album art, song info, a live audio waveform, and playback controls.
- 🔒 **Caps Lock & Num Lock Badges:** Sleek real-time visual overlays triggered instantly on Caps Lock or Num Lock press with automated timeout.
- 🔋 **Premium Battery & Power Alerts:** Beautiful event-driven alerts displaying custom-fluid animated battery icons on plug-in, plug-out, and critical thresholds.
- 🔌 **USB/Device Connections:** Live, automated status alert widgets with custom Direct2D vector plug graphics for USB drive and COM/Bluetooth device connections.
- 🎢 **Asymmetric Spring Physics:** Energetic pop expansion physics (380 stiffness) coupled with organic, smooth dampened glide-back transitions.
- 🖥️ **Windows 11 Fluent Layout:** Toggles on-the-fly into a modern rounded rectangle flyout styling with 1px Fluent borders and dark slate acrylic backgrounds.
- 📊 **Responsive Game Overlay:** Beautifully aligned real-time GPU, CPU, RAM, Disk, and FPS metrics cards that scale dynamically with your screen resolution.
- 📋 **High-Res Clipboard & Notifications:** Instantly preview what you copied or view recent Windows notifications, featuring crisp, high-fidelity 64px application icons extracted dynamically from system executables.
- 🎨 **Customizable Themes:** Switch between sleek OLED Black, Dark Gray, Midnight Blue, Deep Purple, and the premium Fluent Design theme presets, or configure custom Hex accent colors.

---

## ⚙️ Settings & Configuration

You can customize the mod directly through the **Windhawk settings panel**:
- **Position:** Place the island at `Top Center`, `Top Left`, `Top Right`, or `Bottom Center`.
- **Scale:** Scale the widget (`0.8x`, `1.0x`, `1.2x`) to perfectly match your screen resolution and DPI.
- **Windows 11 Style:** Toggle between the classic iPhone Pill style and the modern Windows 11 Fluent flyout style.
- **Accent Color:** Select from Auto (based on album art), System, or Custom Hex codes.
- **Animation Speed:** Adjust between `Slow`, `Normal`, and `Fast` transition speeds.
- **Toggle Modules:** Enable or disable the Media, Clipboard, Battery, Device, Lock Keys, and Progress modules to tailor the experience to your liking.

---

## 🛠️ Technical Details

This mod is compiled using standard C++23 structures and integrates deeply with native Windows components:
- **Direct2D Rendering:** Utilizes hardware acceleration for buttery-smooth animations.
- **Clean COM Implementation:** Solves static analysis include loops and Mingw/Clangd traits mapping.
- **Highly Performance-Optimized:** Rate-limited polling, low-level event hooks, and efficient system event listening keep background CPU usage at near 0%.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

