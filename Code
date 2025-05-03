import React, { useState } from "react";

const outcomes = ["Big", "Small"];
const colors = ["Red", "Green"];

export default function HgzyPredictor() {
  const [history, setHistory] = useState([]);
  const [prediction, setPrediction] = useState(null);

  const addRound = (number, color) => {
    const bigSmall = number >= 5 ? "Big" : "Small";
    const round = { number, color, bigSmall };
    const updated = [...history, round];
    setHistory(updated);
    predictNext(updated);
  };

  const predictNext = (data) => {
    const last = data.slice(-5);
    const smallCount = last.filter(r => r.bigSmall === "Small").length;
    const bigCount = last.length - smallCount;

    const redCount = last.filter(r => r.color === "Red").length;
    const greenCount = last.length - redCount;

    const likelySize = smallCount > bigCount ? "Small" : "Big";
    const likelyColor = redCount > greenCount ? "Red" : "Green";

    setPrediction({ size: likelySize, color: likelyColor });
  };

  return (
    <div className="p-4 max-w-xl mx-auto">
      <h1 className="text-2xl font-bold mb-4">Hgzy Outcome Predictor</h1>

      <div className="grid grid-cols-3 gap-2 mb-4">
        {[...Array(10).keys()].map(n => (
          <button
            key={n}
            className="bg-blue-100 p-2 rounded hover:bg-blue-200"
            onClick={() => addRound(n, n === 0 ? "Red" : n === 5 ? "Green" : Math.random() > 0.5 ? "Red" : "Green")}
          >
            {n}
          </button>
        ))}
      </div>

      {prediction && (
        <div className="bg-green-100 p-4 rounded">
          <h2 className="text-xl font-semibold">Next Likely Outcome</h2>
          <p><strong>Big/Small:</strong> {prediction.size}</p>
          <p><strong>Red/Green:</strong> {prediction.color}</p>
        </div>
      )}

      <div className="mt-6">
        <h3 className="text-lg font-semibold mb-2">History</h3>
        <ul className="list-disc list-inside">
          {history.map((r, i) => (
            <li key={i}>Round {i + 1}: {r.number} - {r.bigSmall} / {r.color}</li>
          ))}
        </ul>
      </div>
    </div>
  );
}
