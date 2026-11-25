import React, { useState, useEffect, useRef } from 'react';
import { Settings, FileText, Plus, Trash2, Printer, Shuffle, Image as ImageIcon } from 'lucide-react';

// --- 初始假資料 (示範圖庫) ---
const initialVocabulary = [
  { id: 1, image: 'https://images.unsplash.com/photo-1560806887-1e4cd0b614d5?auto=format&fit=crop&w=300&q=80', grade: '三年級', semester: '上學期', unit: 'Unit 1', word: 'apple' },
  { id: 2, image: 'https://images.unsplash.com/photo-1528825871115-3581a5387919?auto=format&fit=crop&w=300&q=80', grade: '三年級', semester: '上學期', unit: 'Unit 1', word: 'banana' },
  { id: 3, image: 'https://images.unsplash.com/photo-1514888286974-6c03e2ca1dba?auto=format&fit=crop&w=300&q=80', grade: '三年級', semester: '上學期', unit: 'Unit 1', word: 'cat' },
  { id: 4, image: 'https://images.unsplash.com/photo-1543466835-00a7907e9de1?auto=format&fit=crop&w=300&q=80', grade: '三年級', semester: '上學期', unit: 'Unit 2', word: 'dog' },
  { id: 5, image: 'https://images.unsplash.com/photo-1557050543-4d5f4e07ef46?auto=format&fit=crop&w=300&q=80', grade: '四年級', semester: '下學期', unit: 'Unit 1', word: 'elephant' },
  { id: 6, image: 'https://images.unsplash.com/photo-1583337130417-3346a1be7dee?auto=format&fit=crop&w=300&q=80', grade: '三年級', semester: '上學期', unit: 'Unit 2', word: 'bird' },
];

// --- 輔助元件：英文四線格 (標準 EFL 格式：頂線、中虛線、紅底線、底線) ---
const FourLineGrid = () => (
  <div className="w-full h-14 relative flex flex-col justify-between pt-1 mt-2">
    <div className="w-full border-t border-gray-400"></div>
    <div className="w-full border-t border-dashed border-gray-400 absolute top-1/3 left-0"></div>
    <div className="w-full border-t border-red-500 absolute top-2/3 left-0"></div>
    <div className="w-full border-t border-gray-400 absolute bottom-0 left-0"></div>
  </div>
);

// --- 輔助元件：單一底線 ---
const SingleUnderline = () => (
  <div className="w-full h-14 flex items-end mt-2">
    <div className="w-full border-b-2 border-black"></div>
  </div>
);

export default function App() {
  const [activeTab, setActiveTab] = useState('generator'); // 'admin' 或 'generator'
  const [vocabBank, setVocabBank] = useState(initialVocabulary);
  
  // 考卷生成器狀態
  const [filters, setFilters] = useState({ grade: '全部', semester: '全部', unit: '全部' });
  const [questionCount, setQuestionCount] = useState('全部'); // 新增出題數量狀態
  const [lineStyle, setLineStyle] = useState('four-line'); // 'underline' | 'four-line'
  const [currentQuiz, setCurrentQuiz] = useState([]);

  // 新增單字表單狀態
  const [newVocab, setNewVocab] = useState({
    image: '',
    grade: '三年級',
    semester: '上學期',
    unit: '',
    word: ''
  });
  const fileInputRef = useRef(null);

  // 初始化時自動生成一次預設考卷
  useEffect(() => {
    generateQuiz();
    // eslint-disable-next-line react-hooks/exhaustive-deps
  }, [vocabBank]);

  // 處理圖片上傳 (將本機圖片暫存為 Blob URL 以供預覽與生成)
  const handleImageUpload = (e) => {
    const file = e.target.files[0];
    if (file) {
      const imageUrl = URL.createObjectURL(file);
      setNewVocab({ ...newVocab, image: imageUrl });
    }
  };

  // 新增單字到後台圖庫
  const handleAddVocab = (e) => {
    e.preventDefault();
    if (!newVocab.image || !newVocab.unit || !newVocab.word) {
      alert("請完整填寫圖片、單元與單字！");
      return;
    }
    const newItem = {
      ...newVocab,
      id: Date.now()
    };
    setVocabBank([...vocabBank, newItem]);
    setNewVocab({ ...newVocab, image: '', unit: '', word: '' });
    if (fileInputRef.current) fileInputRef.current.value = ''; // 清空檔案選擇器
  };

  // 刪除圖庫中的單字
  const handleDeleteVocab = (id) => {
    setVocabBank(vocabBank.filter(v => v.id !== id));
  };

  // 取得動態過濾選項 (從現有圖庫中提取)
  const uniqueGrades = ['全部', ...new Set(vocabBank.map(v => v.grade))];
  const uniqueSemesters = ['全部', ...new Set(vocabBank.map(v => v.semester))];
  const uniqueUnits = ['全部', ...new Set(vocabBank.map(v => v.unit))];

  // Fisher-Yates 洗牌演算法 (隨機打亂題目)
  const shuffleArray = (array) => {
    const newArray = [...array];
    for (let i = newArray.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [newArray[i], newArray[j]] = [newArray[j], newArray[i]];
    }
    return newArray;
  };

  // 生成考卷邏輯：篩選並打亂
  const generateQuiz = () => {
    let filtered = vocabBank;
    if (filters.grade !== '全部') filtered = filtered.filter(v => v.grade === filters.grade);
    if (filters.semester !== '全部') filtered = filtered.filter(v => v.semester === filters.semester);
    if (filters.unit !== '全部') filtered = filtered.filter(v => v.unit === filters.unit);

    let shuffled = shuffleArray(filtered);
    
    // 依照設定的題數進行裁切
    if (questionCount !== '全部') {
      shuffled = shuffled.slice(0, parseInt(questionCount, 10));
    }

    setCurrentQuiz(shuffled);
  };

  // 觸發瀏覽器列印
  const handlePrint = () => {
    window.print();
  };

  // 計算分頁 (每頁最多 12 題，排版剛好符合 A4 大小)
  const QUESTIONS_PER_PAGE = 12;
  const pages = [];
  for (let i = 0; i < currentQuiz.length; i += QUESTIONS_PER_PAGE) {
    pages.push(currentQuiz.slice(i, i + QUESTIONS_PER_PAGE));
  }

  return (
    <div className="min-h-screen bg-gray-50 text-gray-800 font-sans">
      {/* 注入列印專用 CSS，隱藏無關 UI 並調整列印邊距 */}
      <style>{`
        @media print {
          body {
            background-color: white;
            -webkit-print-color-adjust: exact;
          }
          .hide-on-print {
            display: none !important;
          }
          .print-page {
            width: 100% !important;
            max-width: none !important;
            margin: 0 !important;
            padding: 0 !important;
            box-shadow: none !important;
            border: none !important;
            aspect-ratio: auto !important;
            page-break-after: always;
          }
          .print-page:last-child {
            page-break-after: auto;
          }
          @page {
            size: A4 portrait;
            margin: 15mm;
          }
        }
      `}</style>

      {/* 頂部導航列 (列印時隱藏) */}
      <div className="bg-white shadow-sm hide-on-print sticky top-0 z-10">
        <div className="max-w-7xl mx-auto px-4">
          <div className="flex space-x-8">
            <button
              onClick={() => setActiveTab('generator')}
              className={`flex items-center px-4 py-4 border-b-2 font-medium transition-colors ${
                activeTab === 'generator' ? 'border-indigo-600 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700'
              }`}
            >
              <FileText className="w-5 h-5 mr-2" />
              考卷生成器
            </button>
            <button
              onClick={() => setActiveTab('admin')}
              className={`flex items-center px-4 py-4 border-b-2 font-medium transition-colors ${
                activeTab === 'admin' ? 'border-indigo-600 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700'
              }`}
            >
              <Settings className="w-5 h-5 mr-2" />
              後台圖庫管理
            </button>
          </div>
        </div>
      </div>

      <div className="max-w-7xl mx-auto px-4 py-8">
        
        {/* ==================== 考卷生成器 (前端) ==================== */}
        {activeTab === 'generator' && (
          <div className="flex flex-col lg:flex-row gap-8 items-start">
            
            {/* 左側控制面板 (列印時隱藏) */}
            <div className="w-full lg:w-1/4 space-y-6 hide-on-print sticky top-24">
              <div className="bg-white p-6 rounded-xl shadow-sm border border-gray-100">
                <h2 className="text-lg font-bold mb-4 flex items-center text-gray-800">
                  <Settings className="w-5 h-5 mr-2 text-indigo-600" />
                  考卷設定
                </h2>
                
                {/* 篩選器 */}
                <div className="space-y-4">
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-1">選擇年級</label>
                    <select 
                      className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                      value={filters.grade}
                      onChange={(e) => setFilters({...filters, grade: e.target.value})}
                    >
                      {uniqueGrades.map(g => <option key={g} value={g}>{g}</option>)}
                    </select>
                  </div>
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-1">選擇學期</label>
                    <select 
                      className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                      value={filters.semester}
                      onChange={(e) => setFilters({...filters, semester: e.target.value})}
                    >
                      {uniqueSemesters.map(s => <option key={s} value={s}>{s}</option>)}
                    </select>
                  </div>
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-1">選擇單元</label>
                    <select 
                      className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                      value={filters.unit}
                      onChange={(e) => setFilters({...filters, unit: e.target.value})}
                    >
                      {uniqueUnits.map(u => <option key={u} value={u}>{u}</option>)}
                    </select>
                  </div>
                  <div>
                    <label className="block text-sm font-medium text-gray-700 mb-1">出題數量</label>
                    <select 
                      className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                      value={questionCount}
                      onChange={(e) => setQuestionCount(e.target.value)}
                    >
                      <option value="10">10 題</option>
                      <option value="20">20 題</option>
                      <option value="30">30 題</option>
                      <option value="40">40 題</option>
                      <option value="全部">全部 (不限制)</option>
                    </select>
                  </div>
                </div>

                <hr className="my-6 border-gray-200" />

                {/* 答題線條樣式切換 */}
                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-3">學生填寫格線</label>
                  <div className="space-y-3">
                    <label className="flex items-center space-x-3 cursor-pointer p-3 border rounded-lg hover:bg-gray-50 transition-colors">
                      <input 
                        type="radio" 
                        name="lineStyle" 
                        value="underline" 
                        checked={lineStyle === 'underline'} 
                        onChange={() => setLineStyle('underline')}
                        className="w-4 h-4 text-indigo-600 focus:ring-indigo-500"
                      />
                      <span className="text-sm font-medium">單一底線</span>
                    </label>
                    <label className="flex items-center space-x-3 cursor-pointer p-3 border rounded-lg hover:bg-gray-50 transition-colors">
                      <input 
                        type="radio" 
                        name="lineStyle" 
                        value="four-line" 
                        checked={lineStyle === 'four-line'} 
                        onChange={() => setLineStyle('four-line')}
                        className="w-4 h-4 text-indigo-600 focus:ring-indigo-500"
                      />
                      <span className="text-sm font-medium">英文四線格</span>
                    </label>
                  </div>
                </div>

                <hr className="my-6 border-gray-200" />

                {/* 動作按鈕 */}
                <div className="space-y-3">
                  <button 
                    onClick={generateQuiz}
                    className="w-full py-2.5 bg-indigo-600 hover:bg-indigo-700 text-white rounded-lg font-medium flex items-center justify-center transition-colors shadow-sm"
                  >
                    <Shuffle className="w-4 h-4 mr-2" />
                    隨機產生 ({currentQuiz.length} 題)
                  </button>
                  <button 
                    onClick={handlePrint}
                    disabled={currentQuiz.length === 0}
                    className="w-full py-2.5 bg-emerald-600 hover:bg-emerald-700 text-white rounded-lg font-medium flex items-center justify-center transition-colors shadow-sm disabled:opacity-50 disabled:cursor-not-allowed"
                  >
                    <Printer className="w-4 h-4 mr-2" />
                    列印 A4 考卷
                  </button>
                </div>
              </div>
            </div>

            {/* 右側 A4 考卷預覽區 */}
            <div className="w-full lg:w-3/4 flex flex-col items-center overflow-x-auto space-y-8 pb-10">
              
              {/* 考卷內容區塊 */}
              {currentQuiz.length === 0 ? (
                <div className="flex flex-col items-center justify-center h-64 text-gray-400 hide-on-print w-full bg-white rounded-xl border border-gray-200">
                  <ImageIcon className="w-16 h-16 mb-4 opacity-30" />
                  <p>目前沒有符合條件的單字，請調整左側篩選器或至後台新增。</p>
                </div>
              ) : (
                pages.map((pageData, pageIndex) => (
                  <div key={pageIndex} className="print-page bg-white shadow-xl w-full max-w-[210mm] aspect-[1/1.414] p-10 md:p-14 relative border border-gray-200 flex flex-col">
                    
                    {/* 考卷表頭 */}
                    <div className="text-center mb-6 border-b-2 border-gray-800 pb-4 shrink-0">
                      <h1 className="text-3xl font-bold mb-4 tracking-widest text-gray-900">
                        英語單字小考 {pages.length > 1 && <span className="text-xl font-normal ml-2 tracking-normal text-gray-600">(P. {pageIndex + 1})</span>}
                      </h1>
                      <div className="flex justify-between items-end text-lg font-medium px-2">
                        <div className="flex space-x-6">
                          <span>年級：<span className="inline-block w-16 border-b border-gray-800 text-center">{filters.grade === '全部' ? '' : filters.grade}</span></span>
                          <span>班級：<span className="inline-block w-16 border-b border-gray-800"></span></span>
                          <span>座號：<span className="inline-block w-16 border-b border-gray-800"></span></span>
                          <span>姓名：<span className="inline-block w-32 border-b border-gray-800"></span></span>
                        </div>
                        <div>
                          {pageIndex === 0 ? (
                            <span>分數：<span className="inline-block w-24 border-b border-gray-800 text-center text-red-600 text-2xl font-bold"></span></span>
                          ) : (
                            <span className="inline-block w-24"></span> /* 保持排版對齊 */
                          )}
                        </div>
                      </div>
                    </div>

                    <div className="grid grid-cols-2 gap-x-12 gap-y-10 flex-grow content-start">
                      {pageData.map((item, index) => {
                        const globalIndex = pageIndex * QUESTIONS_PER_PAGE + index + 1;
                        return (
                          <div key={item.id} className="flex items-center space-x-4 break-inside-avoid">
                            {/* 題號與圖片 */}
                            <div className="flex items-center space-x-3 w-[45%]">
                              <span className="font-bold text-xl">{globalIndex}.</span>
                              <div className="w-24 h-24 border-2 border-gray-300 rounded-lg overflow-hidden flex-shrink-0 flex items-center justify-center bg-white shadow-sm p-1">
                                <img src={item.image} alt="Quiz Item" className="max-w-full max-h-full object-contain mix-blend-multiply" />
                              </div>
                            </div>
                            
                            {/* 填寫區 */}
                            <div className="w-[55%] pb-2">
                              {lineStyle === 'four-line' ? <FourLineGrid /> : <SingleUnderline />}
                            </div>
                          </div>
                        );
                      })}
                    </div>
                  </div>
                ))
              )}
            </div>
          </div>
        )}

        {/* ==================== 後台圖庫管理 (後台) ==================== */}
        {activeTab === 'admin' && (
          <div className="space-y-8 hide-on-print max-w-5xl mx-auto">
            
            {/* 新增單字表單 */}
            <div className="bg-white p-8 rounded-xl shadow-sm border border-gray-100">
              <h2 className="text-xl font-bold mb-6 flex items-center text-gray-800">
                <Plus className="w-5 h-5 mr-2 text-indigo-600" />
                新增單字至圖庫
              </h2>
              <form onSubmit={handleAddVocab} className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-6 gap-6 items-end">
                
                <div className="lg:col-span-2">
                  <label className="block text-sm font-medium text-gray-700 mb-1">上傳圖片</label>
                  <input 
                    type="file" 
                    accept="image/*"
                    ref={fileInputRef}
                    onChange={handleImageUpload}
                    className="block w-full text-sm text-gray-500 file:mr-4 file:py-2 file:px-4 file:rounded-lg file:border-0 file:text-sm file:font-semibold file:bg-indigo-50 file:text-indigo-700 hover:file:bg-indigo-100 border border-gray-200 rounded-lg p-1 transition-colors"
                  />
                  {newVocab.image && (
                    <div className="mt-3 w-20 h-20 border rounded-lg overflow-hidden flex items-center justify-center bg-gray-50">
                      <img src={newVocab.image} alt="Preview" className="max-w-full max-h-full object-contain" />
                    </div>
                  )}
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">年級</label>
                  <select 
                    className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                    value={newVocab.grade}
                    onChange={(e) => setNewVocab({...newVocab, grade: e.target.value})}
                  >
                    {['一年級', '二年級', '三年級', '四年級', '五年級', '六年級'].map(g => <option key={g} value={g}>{g}</option>)}
                  </select>
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">學期</label>
                  <select 
                    className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                    value={newVocab.semester}
                    onChange={(e) => setNewVocab({...newVocab, semester: e.target.value})}
                  >
                    <option value="上學期">上學期</option>
                    <option value="下學期">下學期</option>
                  </select>
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">單元</label>
                  <input 
                    type="text" 
                    placeholder="例: Unit 1"
                    className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                    value={newVocab.unit}
                    onChange={(e) => setNewVocab({...newVocab, unit: e.target.value})}
                  />
                </div>

                <div>
                  <label className="block text-sm font-medium text-gray-700 mb-1">英文單字解答</label>
                  <input 
                    type="text" 
                    placeholder="例: apple"
                    className="w-full p-2 border rounded-lg bg-gray-50 focus:ring-2 focus:ring-indigo-500 outline-none"
                    value={newVocab.word}
                    onChange={(e) => setNewVocab({...newVocab, word: e.target.value})}
                  />
                </div>

                <div className="lg:col-span-6 flex justify-end mt-2">
                  <button 
                    type="submit"
                    className="px-6 py-2.5 bg-indigo-600 hover:bg-indigo-700 text-white rounded-lg font-medium transition-colors shadow-sm flex items-center"
                  >
                    <Plus className="w-4 h-4 mr-2" />
                    新增至圖庫
                  </button>
                </div>
              </form>
            </div>

            {/* 現有圖庫列表 */}
            <div className="bg-white p-8 rounded-xl shadow-sm border border-gray-100">
              <h2 className="text-xl font-bold mb-6 flex items-center text-gray-800">
                <ImageIcon className="w-5 h-5 mr-2 text-indigo-600" />
                目前圖庫清單 (共 {vocabBank.length} 筆)
              </h2>
              <div className="overflow-x-auto rounded-lg border border-gray-200">
                <table className="w-full text-left border-collapse">
                  <thead>
                    <tr className="bg-gray-50 border-b border-gray-200">
                      <th className="p-4 font-semibold text-gray-600">圖片</th>
                      <th className="p-4 font-semibold text-gray-600">年級</th>
                      <th className="p-4 font-semibold text-gray-600">學期</th>
                      <th className="p-4 font-semibold text-gray-600">單元</th>
                      <th className="p-4 font-semibold text-gray-600">單字解答</th>
                      <th className="p-4 font-semibold text-gray-600 text-center">操作</th>
                    </tr>
                  </thead>
                  <tbody className="divide-y divide-gray-100">
                    {vocabBank.map(item => (
                      <tr key={item.id} className="hover:bg-gray-50/50 transition-colors">
                        <td className="p-4">
                          <div className="w-14 h-14 bg-white border border-gray-200 rounded-lg flex items-center justify-center p-1">
                            <img src={item.image} alt={item.word} className="max-w-full max-h-full object-contain" />
                          </div>
                        </td>
                        <td className="p-4 text-gray-700 font-medium">{item.grade}</td>
                        <td className="p-4 text-gray-700 font-medium">{item.semester}</td>
                        <td className="p-4">
                          <span className="bg-indigo-50 text-indigo-700 px-3 py-1 rounded-full text-xs font-semibold tracking-wide">
                            {item.unit}
                          </span>
                        </td>
                        <td className="p-4 font-bold text-gray-900 text-lg">{item.word}</td>
                        <td className="p-4 text-center">
                          <button 
                            onClick={() => handleDeleteVocab(item.id)}
                            className="p-2 text-red-500 hover:bg-red-50 hover:text-red-600 rounded-lg transition-colors"
                            title="刪除"
                          >
                            <Trash2 className="w-5 h-5 mx-auto" />
                          </button>
                        </td>
                      </tr>
                    ))}
                    {vocabBank.length === 0 && (
                      <tr>
                        <td colSpan="6" className="p-12 text-center text-gray-500">
                          目前圖庫沒有任何單字，請從上方表單新增。
                        </td>
                      </tr>
                    )}
                  </tbody>
                </table>
              </div>
            </div>

          </div>
        )}
      </div>
    </div>
  );
}