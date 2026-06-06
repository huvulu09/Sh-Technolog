<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>碩享科技 - 經銷商業務大廳</title>
    <!-- 引入 React, ReactDOM 和 Tailwind 的 CDN，讓 HTML 直接變成 App -->
    <script src="https://unpkg.com/react@18/umd/react.production.min.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body>
    <div id="root"></div>
    <script type="text/babel">
        // 這是整合後的完整程式碼，直接在瀏覽器運作
        const { useState, useMemo } = React;
        
        function App() {
            const [activeTab, setActiveTab] = useState('home');
            const [price, setPrice] = useState('45000');
            const [beds, setBeds] = useState('10');

            return (
                <div className="flex h-screen bg-slate-100">
                    <nav className="w-20 bg-slate-900 flex flex-col items-center py-8 text-white">
                        <div className="mb-10 font-bold text-sky-400">碩享</div>
                        {['首頁', '試算', 'CRM'].map(item => (
                            <button key={item} onClick={() => setActiveTab(item)} className="p-4 hover:bg-slate-700 w-full text-xs">
                                {item}
                            </button>
                        ))}
                    </nav>
                    <main className="flex-1 p-8 overflow-y-auto">
                        <h1 className="text-2xl font-bold mb-6">{activeTab === '首頁' ? '歡迎回來，王總監' : activeTab + '功能'}</h1>
                        {activeTab === '試算' && (
                            <div className="bg-white p-6 rounded-xl shadow">
                                <label className="block mb-2">產品價格</label>
                                <input type="number" value={price} onChange={e => setPrice(e.target.value)} className="w-full p-2 border mb-4" />
                                <label className="block mb-2">床數</label>
                                <input type="number" value={beds} onChange={e => setBeds(e.target.value)} className="w-full p-2 border mb-4" />
                                <div className="text-xl font-bold text-sky-600">總獲利試算: NT$ {(price * beds * 0.3).toLocaleString()}</div>
                            </div>
                        )}
                    </main>
                </div>
            );
        }
        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
