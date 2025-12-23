# Party Playlist 🎵

A collaborative, real-time music queue application designed for weddings and parties. Guests can suggest songs via a simplified interface, while the host maintains full control over playback and the queue.

**Live Demo:** [https://party-playlist-seven.vercel.app/](https://party-playlist-seven.vercel.app/)

## ✨ Features

### 👤 Guest Experience
- **Simple Access:** Join the party using a 4-digit PIN (`2502`).
- **Search & Add:** Search YouTube for songs and add them to the shared queue.
- **Smart Queue:** View "Now Playing" and "Up Next" songs in real-time.
- **Fair Play:** Rate limiting prevents spam (max 5 songs/minute) and duplicate detection prevents repeat adds.
- **Duration Limit:** Only allows adding songs under 8 minutes to keep the vibe moving.

### 🎧 Host & Admin
- **Secure Control:** Host access protected by a separate PIN (`2508`).
- **Music Player:** Hidden YouTube player with custom controls (Play/Pause, Previous, Skip).
- **Queue Management:**
    - **Prioritize:** "Play Next" feature to bump requested songs to the top.
    - **Remove:** Delete songs from the queue.
    - **Clear:** Emergency "Clear Playlist" button.
- **Playlist Seeding:** Import entire YouTube playlists to populate the queue instantly.
- **History:** View a list of recently played tracks.

## 🛠️ Technology Stack

- **Frontend:** [React](https://react.dev/) + [Vite](https://vitejs.dev/) - Fast, modern UI development.
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) - Responsive, beautiful design with glassmorphism effects.
- **Icons:** [Lucide React](https://lucide.dev/) - Clean, consistent iconography.
- **Backend / Database:** [Firebase](https://firebase.google.com/)
    - **Firestore:** Real-time database for syncing the queue across all devices instanly.
    - **Authentication:** Firebase Anonymous Auth to handle session security (PIN-gated access).
- **Media:** [YouTube Data API v3](https://developers.google.com/youtube/v3) & IFrame API - For searching songs and playback.

## 📂 Project Structure

```bash
src/
├── App.jsx       # Main application logic, routing, and state management
├── apps/         # (Optional) Additional components
├── index.css     # Global styles and Tailwind directives
└── main.jsx      # Entry point
```

### Key Components (`App.jsx`)
- **`PinGate`**: Handles the initial PIN entry and authentication.
- **`GuestView`**: The interface for guests to search and add songs.
- **`HostView`**: The admin interface with player controls and queue management.

## 🚀 Getting Started

### Prerequisites
- Node.js (v18+)
- Firebase Project
- Google Cloud Project with YouTube Data API v3 enabled

### Installation

1.  **Clone the repository**
    ```bash
    git clone https://github.com/KshitijRanjan/party-playlist.git
    cd party-playlist
    ```

2.  **Install dependencies**
    ```bash
    npm install
    ```

3.  **Environment Setup**
    Create a `.env` file in the root directory:
    ```env
    VITE_YOUTUBE_API_KEY="AIzaSy..."
    ```

4.  **Run Locally**
    ```bash
    npm run dev
    ```

## 🔒 Security & Data Strategy

- **Real-time Sync:** The app uses Firebase Firestore `onSnapshot` listeners to ensure that when a guest adds a song, it appears on the Host's screen immediately without refreshing.
- **Access Control:**
    - **Guests** (`PIN: 2502`) have restricted write access (can only add to queue).
    - **Hosts** (`PIN: 2508`) have full management capabilities.
    - *Note: Current implementation uses client-side routing gates. For production, strict Firestore Security Rules are recommended.*

## 🤝 Contributing

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

Built with ❤️ for the perfect party atmosphere.
