# special_stepimport React, { useState } from "react";
import { FaSearch, FaShoppingCart, FaFacebook, FaInstagram, FaTiktok } from "react-icons/fa";
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";

const categories = ["جميع الأحذية", "رياضي", "كاجوال", "رسمي"];

const products = [
  { id: 1, name: "حذاء رياضي", category: "رياضي", price: "120 ريال", image: "https://via.placeholder.com/150", description: "حذاء رياضي مريح وخفيف الوزن مناسب للجري والتمارين الرياضية.", rating: 4.5 },
  { id: 2, name: "حذاء كاجوال", category: "كاجوال", price: "150 ريال", image: "https://via.placeholder.com/150", description: "حذاء كاجوال أنيق يناسب جميع الإطلالات اليومية.", rating: 4.2 },
  { id: 3, name: "حذاء رسمي", category: "رسمي", price: "200 ريال", image: "https://via.placeholder.com/150", description: "حذاء رسمي فاخر مصنوع من الجلد الطبيعي لمظهر أنيق.", rating: 4.8 },
];

const Home = () => {
  const [selectedCategory, setSelectedCategory] = useState("جميع الأحذية");
  const [searchQuery, setSearchQuery] = useState("");

  const filteredProducts = products.filter(product => 
    (selectedCategory === "جميع الأحذية" || product.category === selectedCategory) &&
    product.name.includes(searchQuery)
  );

  return (
    <div className="min-h-screen bg-blue-900 text-white">
      <header className="bg-blue-800 shadow-md p-4 flex justify-between items-center">
        <h1 className="text-2xl font-bold text-blue-300">Special Step</h1>
        <div className="flex items-center gap-4">
          <input
            type="text"
            placeholder="ابحث عن حذاء..."
            value={searchQuery}
            onChange={(e) => setSearchQuery(e.target.value)}
            className="border px-2 py-1 rounded-md text-blue-900"
          />
          <FaSearch className="text-blue-300 cursor-pointer" size={20} />
          <FaShoppingCart className="text-blue-300 cursor-pointer" size={20} />
        </div>
      </header>

      <section className="bg-blue-700 text-white text-center py-16">
        <h2 className="text-4xl font-bold">مرحبًا بكم في "الخطوة الخاصة" – حيث تبدأ رحلتك بالإنترنت!</h2>
        <p className="mt-2 text-lg">نقدم لكم مجموعة مختارة من الأحذية العصرية التي تجمع بين الأنواع المتنوعة من كل الأذواق. في "الخطوة الخاصة"، نؤمن بأن كل خطوة الإيمان بشخصيتك، لذلك نوفر لك تشكيلة متنوعة من تلك الأحذية</p>
        <p className="mt-2 text-lg">استمتعوا بتصفح مجموعاتنا المميزة، واختاروا ما يناسبكم بكل سهولة وراحه. لأن خطواتك تستحق العناء، "الخطوة الخاصة" هو اختيارك!</p>
      </section>

      <footer className="bg-blue-800 text-center p-4 mt-8">
        <p className="text-lg">📞 للتواصل: 123-456-789</p>
        <div className="flex justify-center gap-4 mt-2">
          <a href="#" className="text-white text-2xl hover:text-blue-400"><FaFacebook /></a>
          <a href="#" className="text-white text-2xl hover:text-blue-400"><FaInstagram /></a>
          <a href="#" className="text-white text-2xl hover:text-blue-400"><FaTiktok /></a>
        </div>
      </footer>
    </div>
  );
};

const App = () => {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<Home />} />
      </Routes>
    </Router>
  );
};

export default App;
