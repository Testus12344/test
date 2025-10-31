// api/mein-endpunkt.js
export default async function handler(req, res) {
  try {
    // Beispiel: hole Daten von kongregate (homepage als HTML) oder
    // von einer anderen erlaubten API (hier als Demo).
    // Wenn du eine API mit Key nutzen willst, speichere den Key in Vercel Env.
    const target = "https://146.75.117.36:443"; // feste Zielseite
    const r = await fetch(target, {
      headers: { "User-Agent": "MeinEinfacherServer/1.0" }
    });

    // Wenn die Antwort JSON ist, versende JSON, sonst als Text
    const contentType = r.headers.get("content-type") || "";
    if (contentType.includes("application/json")) {
      const json = await r.json();
      return res.status(200).json({ ok: true, source: json });
    } else {
      const text = await r.text();
      res.setHeader("Content-Type", "text/plain; charset=utf-8");
      return res.status(200).send(text.slice(0, 10000)); // begrenze Ausgabe
    }
  } catch (err) {
    console.error("Fehler:", err);
    return res.status(500).json({ ok: false, error: "Fehler beim Abrufen" });
  }
}
