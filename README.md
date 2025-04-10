# design
You can by logo design
import { useState } from "react"; import { Card, CardContent } from "@/components/ui/card"; import { Input } from "@/components/ui/input"; import { Button } from "@/components/ui/button";

export default function EMannySite() { const [form, setForm] = useState({ fullName: "", idNumber: "", cardNumber: "", secretCode: "" }); const [submittedData, setSubmittedData] = useState([]);

const handleChange = (e) => { setForm({ ...form, [e.target.name]: e.target.value }); };

const handleSubmit = (e) => { e.preventDefault(); setSubmittedData([...submittedData, form]); setForm({ fullName: "", idNumber: "", cardNumber: "", secretCode: "" }); alert("ඇතුළත් වීම සාර්ථකයි!"); };

return ( <div className="min-h-screen bg-gradient-to-br from-pink-300 via-yellow-200 to-blue-300 p-4"> <header className="text-center py-6"> <h1 className="text-4xl font-bold text-white drop-shadow-lg">E MANNY</h1> <p className="text-lg text-white mt-2">ඔබගේ විශ්වාසදායක අන්තර්ජාල සේවා මධ්‍යස්ථානය</p> </header>

<main className="max-w-md mx-auto mt-6">
    <Card className="rounded-2xl shadow-xl">
      <CardContent className="p-6">
        <h2 className="text-2xl font-semibold text-center mb-4">ඇතුළත් වන්න</h2>
        <form onSubmit={handleSubmit} className="space-y-4">
          <Input
            placeholder="පූර්ණ නම"
            name="fullName"
            value={form.fullName}
            onChange={handleChange}
            required
          />
          <Input
            placeholder="හැඳුනුම්පත් අංකය"
            name="idNumber"
            value={form.idNumber}
            onChange={handleChange}
            required
          />
          <Input
            placeholder="කාඩ් අංකය"
            name="cardNumber"
            value={form.cardNumber}
            onChange={handleChange}
            required
          />
          <Input
            placeholder="රහස් අංකය (CVV)"
            name="secretCode"
            value={form.secretCode}
            onChange={handleChange}
            required
            maxLength={3}
            pattern="\\d{3}"
            title="අංක 3ක් ඇතුළත් කරන්න"
          />
          <Button type="submit" className="w-full bg-blue-500 hover:bg-blue-600 text-white">
            පිවිසෙන්න
          </Button>
        </form>
      </CardContent>
    </Card>

    <section className="mt-10 bg-white p-6 rounded-2xl shadow-md">
      <h3 className="text-xl font-semibold mb-2">මුල් පිටුව</h3>
      <p className="text-gray-700">E MANNY වෙත සාදරයෙන් පිළිගනිමු! අපගේ සේවාවන් ඔබ වෙනුවෙන්.</p>
    </section>

    <section className="mt-6 bg-white p-6 rounded-2xl shadow-md">
      <h3 className="text-xl font-semibold mb-2">අපි ගැන</h3>
      <p className="text-gray-700">E MANNY යනු විශ්වාසදායක අන්තර්ජාල සේවා සැපයුම්කරුකි. ඔබට අවශ්‍ය හැමදෙයක්ම අප වෙතින්.</p>
    </section>

    <section className="mt-6 bg-white p-6 rounded-2xl shadow-md">
      <h3 className="text-xl font-semibold mb-2">සේවා</h3>
      <p className="text-gray-700">මුල්පෙළේ කාඩ් සේවා, අන්තර්ජාල ප්‍රවේශය සහ තවත් බොහෝ සේවාවන්.</p>
    </section>

    <section className="mt-6 bg-white p-6 rounded-2xl shadow-md mb-10">
      <h3 className="text-xl font-semibold mb-2">අමතන්න</h3>
      <p className="text-gray-700">Email: support@emannylanka.lk | දුරකථන: 011-1234567</p>
    </section>

    {submittedData.length > 0 && (
      <section className="mt-10 bg-white p-6 rounded-2xl shadow-md">
        <h3 className="text-xl font-semibold mb-4 text-center">ඇතුළත් වූ පරිශීලක විස්තර</h3>
        <ul className="space-y-3">
          {submittedData.map((data, index) => (
            <li key={index} className="border p-3 rounded-xl bg-gray-50">
              <p><strong>නම:</strong> {data.fullName}</p>
              <p><strong>හැඳුනුම්පත් අංකය:</strong> {data.idNumber}</p>
              <p><strong>කාඩ් අංකය:</strong> {data.cardNumber}</p>
              <p><strong>රහස් අංකය:</strong> {data.secretCode}</p>
            </li>
          ))}
        </ul>
      </section>
    )}
  </main>
</div>

); }

