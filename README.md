npm create vite@latest visa-app -- --template react
cd visa-app
npm install
npm install react-router-dom
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p

export default {
content: ["./index.html", "./src/**/*.{js,jsx}"],
theme: {
extend: {
colors: {
primary: "#2563EB"
}
}
},
plugins: [],
}

@tailwind base;
@tailwind components;
@tailwind utilities;

src/
├── pages/
│ ├── Home.jsx
│ ├── TravelDetails.jsx
│ ├── Documents.jsx
│ ├── CoverLetter.jsx
│ ├── Review.jsx
├── components/
│ ├── Stepper.jsx
│ ├── Card.jsx
├── App.jsx
└── main.jsx

import { BrowserRouter, Routes, Route } from "react-router-dom";
import Home from "./pages/Home";
import TravelDetails from "./pages/TravelDetails";
import Documents from "./pages/Documents";
import CoverLetter from "./pages/CoverLetter";
import Review from "./pages/Review";

export default function App() {
return (
<BrowserRouter>
<Routes>
<Route path="/" element={<Home />} />
<Route path="/travel" element={<TravelDetails />} />
<Route path="/documents" element={<Documents />} />
<Route path="/cover-letter" element={<CoverLetter />} />
<Route path="/review" element={<Review />} />
</Routes>
</BrowserRouter>
);
}

import { useNavigate } from "react-router-dom";

export default function Home() {
const navigate = useNavigate();

return (
<div className="min-h-screen bg-gray-50">
<div className="max-w-5xl mx-auto p-6">
<h1 className="text-3xl font-bold mb-4">Plan your Trip</h1>

<div className="bg-white p-6 rounded-xl shadow">
<label className="block mb-2 font-medium">Destination</label>
<select className="w-full border p-3 rounded">
<option>Dubai</option>
<option>Singapore</option>
</select>

<button
onClick={() => navigate("/travel")}
className="mt-6 bg-primary text-white px-6 py-3 rounded w-full"
>
Continue
</button>
</div>
</div>
</div>
);
}

import { useNavigate } from "react-router-dom";

export default function TravelDetails() {
const navigate = useNavigate();

return (
<div className="min-h-screen bg-gray-50 p-6">
<div className="max-w-4xl mx-auto bg-white p-6 rounded-xl shadow">
<h2 className="text-xl font-semibold mb-4">Travel Details</h2>

<input className="w-full border p-3 mb-3 rounded" placeholder="From City" />
<input className="w-full border p-3 mb-3 rounded" placeholder="To City" />
<input type="date" className="w-full border p-3 mb-3 rounded" />

<button
onClick={() => navigate("/documents")}
className="bg-primary text-white px-6 py-3 rounded w-full"
>
Next
</button>
</div>
</div>
);
}

import { useNavigate } from "react-router-dom";

export default function Documents() {
const navigate = useNavigate();

return (
<div className="min-h-screen bg-gray-50 p-6">
<div className="max-w-4xl mx-auto bg-white p-6 rounded-xl shadow">
<h2 className="text-xl font-semibold mb-4">Upload Documents</h2>

<input type="file" className="mb-4" />
<input type="file" className="mb-4" />

<button
onClick={() => navigate("/cover-letter")}
className="bg-primary text-white px-6 py-3 rounded w-full"
>
Generate Cover Letter
</button>
</div>
</div>
);
}

import { useNavigate } from "react-router-dom";

export default function CoverLetter() {
const navigate = useNavigate();

return (
<div className="min-h-screen bg-gray-50 p-6">
<div className="max-w-5xl mx-auto bg-white p-6 rounded-xl shadow">
<h2 className="text-xl font-semibold mb-4">
Cover Letter for Visa Application
</h2>

<textarea
className="w-full h-80 border p-4 rounded mb-4"
defaultValue={`Dear Visa Officer,

I am applying for a tourist visa to Dubai. I intend to travel for leisure and tourism...

Sincerely,
Applicant`}
/>

<div className="flex gap-4">
<button className="border px-6 py-3 rounded w-full">
Edit
</button>
<button
onClick={() => navigate("/review")}
className="bg-primary text-white px-6 py-3 rounded w-full"
>
Next
</button>
</div>
</div>
</div>
);
}

export default function Review() {
return (
<div className="min-h-screen bg-gray-50 p-6">
<div className="max-w-4xl mx-auto bg-white p-6 rounded-xl shadow">
<h2 className="text-xl font-semibold mb-4">Review Application</h2>

<ul className="mb-6 text-gray-700">
<li>✔ Destination: Dubai</li>
<li>✔ Documents Uploaded</li>
<li>✔ Cover Letter Generated</li>
</ul>

<button className="bg-green-600 text-white px-6 py-3 rounded w-full">
Submit Application
</button>
</div>
</div>
);
}


