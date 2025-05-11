```jsx
import { useState } from "react";

export default function App() {
  const [formData, setFormData] = useState({
    playerName: "",
    inGameId: "",
    rank: "",
    playTime: "",
    preferredRole: "",
    notes: "",
  });

  const handleChange = (e) => {
    const { name, value } = e.target;
    setFormData((prev) => ({ ...prev, [name]: value }));
  };

  const handleSubmit = (e) => {
    e.preventDefault();

    // Create a WhatsApp message with the form data
    const message = encodeURIComponent(`
Player Name: ${formData.playerName}
In-Game ID: ${formData.playerName}#${formData.inGameId}
Rank: ${formData.rank}
Play Time: ${formData.playTime}
Preferred Role: ${formData.preferredRole}
Notes: ${formData.notes}
`);

    // Redirect to WhatsApp with the predefined number and message
    window.open(
      `https://wa.me/972535367269?text=${message}`,
      "_blank"
    );
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-blue-900 via-purple-900 to-indigo-900 text-white">
      {/* Header */}
      <header className="py-6 px-4 md:px-8 flex justify-between items-center border-b border-gray-700">
        <h1 className="text-2xl font-bold tracking-wide">PUBG Player Registration</h1>
        <img
          src="https://placehold.co/40x40/ffcc00/000000?text=PG"
          alt="PUBG Logo"
          className="rounded-md shadow-lg"
        />
      </header>

      {/* Main Content */}
      <main className="max-w-3xl mx-auto py-12 px-4 md:px-8">
        <div className="bg-black/30 backdrop-blur-sm rounded-xl p-6 md:p-10 shadow-2xl border border-gray-700 transition-transform duration-300 hover:scale-[1.01]">
          <h2 className="text-3xl font-semibold mb-2">Join Our PUBG Team</h2>
          <p className="text-gray-300 mb-8">
            Fill out your details below and we'll contact you via WhatsApp.
          </p>

          <form onSubmit={handleSubmit} className="space-y-6">
            <div>
              <label htmlFor="playerName" className="block text-sm font-medium text-gray-300 mb-1">
                Player Name
              </label>
              <input
                type="text"
                id="playerName"
                name="playerName"
                value={formData.playerName}
                onChange={handleChange}
                required
                className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white placeholder-gray-500"
                placeholder="Enter your in-game name"
              />
            </div>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label htmlFor="inGameId" className="block text-sm font-medium text-gray-300 mb-1">
                  In-Game ID
                </label>
                <input
                  type="text"
                  id="inGameId"
                  name="inGameId"
                  value={formData.inGameId}
                  onChange={handleChange}
                  required
                  className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white placeholder-gray-500"
                  placeholder="####"
                />
              </div>

              <div>
                <label htmlFor="rank" className="block text-sm font-medium text-gray-300 mb-1">
                  Current Rank
                </label>
                <select
                  id="rank"
                  name="rank"
                  value={formData.rank}
                  onChange={handleChange}
                  required
                  className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white"
                >
                  <option value="" disabled>
                    Select your rank
                  </option>
                  <option value="Bronze">Bronze</option>
                  <option value="Silver">Silver</option>
                  <option value="Gold">Gold</option>
                  <option value="Platinum">Platinum</option>
                  <option value="Diamond">Diamond</option>
                  <option value="Master">Master</option>
                  <option value="Grandmaster">Grandmaster</option>
                </select>
              </div>
            </div>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label htmlFor="playTime" className="block text-sm font-medium text-gray-300 mb-1">
                  Preferred Play Time
                </label>
                <input
                  type="text"
                  id="playTime"
                  name="playTime"
                  value={formData.playTime}
                  onChange={handleChange}
                  required
                  className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white placeholder-gray-500"
                  placeholder="e.g., Evening / Weekend Only"
                />
              </div>

              <div>
                <label htmlFor="preferredRole" className="block text-sm font-medium text-gray-300 mb-1">
                  Preferred Role
                </label>
                <select
                  id="preferredRole"
                  name="preferredRole"
                  value={formData.preferredRole}
                  onChange={handleChange}
                  required
                  className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white"
                >
                  <option value="" disabled>
                    Choose role
                  </option>
                  <option value="Leader">Leader</option>
                  <option value="Support">Support</option>
                  <option value="Sniper">Sniper</option>
                  <option value="Flanker">Flanker</option>
                  <option value="Medic">Medic</option>
                  <option value="Other">Other</option>
                </select>
              </div>
            </div>

            <div>
              <label htmlFor="notes" className="block text-sm font-medium text-gray-300 mb-1">
                Additional Notes
              </label>
              <textarea
                id="notes"
                name="notes"
                value={formData.notes}
                onChange={handleChange}
                rows="4"
                className="w-full px-4 py-3 bg-gray-800 border border-gray-600 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 text-white placeholder-gray-500"
                placeholder="Any other info about your PUBG experience..."
              ></textarea>
            </div>

            <button
              type="submit"
              className="w-full mt-4 py-3 px-6 bg-gradient-to-r from-green-500 to-emerald-600 text-white font-semibold rounded-md shadow-md hover:shadow-lg transform hover:-translate-y-0.5 transition-all duration-200"
            >
              Send My Details via WhatsApp
            </button>
          </form>
        </div>

        {/* Decorative Elements */}
        <div className="mt-12 text-center text-gray-500 text-sm">
          <p>© 2025 PUBG Recruitment | Powered by React & TailwindCSS</p>
        </div>
      </main>
    </div>
  );
}
```
