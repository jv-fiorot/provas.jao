<!doctype html>
<html lang="pt-BR" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>João Café - Provas</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&amp;family=Source+Sans+3:wght@400;500;600&amp;display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; }
    html, body { height: 100%; margin: 0; padding: 0; }
    .font-display { font-family: 'Playfair Display', serif; }
    .font-body { font-family: 'Source Sans 3', sans-serif; }
    
    .question-card {
      transition: all 0.2s ease;
    }
    .question-card:hover {
      transform: translateY(-2px);
      box-shadow: 0 8px 25px rgba(139, 90, 43, 0.15);
    }
    
    .tag {
      transition: all 0.15s ease;
    }
    .tag:hover {
      transform: scale(1.05);
    }
    
    .btn-primary {
      transition: all 0.2s ease;
    }
    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 4px 12px rgba(139, 90, 43, 0.3);
    }
    
    .modal-backdrop {
      animation: fadeIn 0.2s ease;
    }
    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }
    
    .modal-content {
      animation: slideUp 0.3s ease;
    }
    @keyframes slideUp {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .toast {
      animation: slideIn 0.3s ease, fadeOut 0.3s ease 2.7s forwards;
    }
    @keyframes slideIn {
      from { transform: translateX(100%); opacity: 0; }
      to { transform: translateX(0); opacity: 1; }
    }
    @keyframes fadeOut {
      from { opacity: 1; }
      to { opacity: 0; }
    }

    .dropdown-menu {
      animation: dropDown 0.2s ease;
    }
    @keyframes dropDown {
      from { opacity: 0; transform: translateY(-10px); }
      to { opacity: 1; transform: translateY(0); }
    }
  </style>
  <style>body { box-sizing: border-box; }</style>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js" type="text/javascript"></script>
 </head>
 <body class="h-full font-body bg-amber-50 text-stone-800 overflow-auto">
  <div id="app" class="min-h-full w-full flex flex-col"><!-- Header -->
   <header class="bg-white border-b border-amber-200 shadow-sm sticky top-0 z-40">
    <div class="max-w-6xl mx-auto px-4 py-4 flex items-center justify-between">
     <div class="flex items-center gap-3"><!-- Coffee Cup SVG Logo -->
      <svg viewbox="0 0 64 64" class="w-12 h-12" fill="none"><!-- Steam lines --> <path d="M20 8 Q22 4 20 0" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
        <animate attributename="d" values="M20 8 Q22 4 20 0;M20 8 Q18 4 20 0;M20 8 Q22 4 20 0" dur="2s" repeatcount="indefinite" />
       </path> <path d="M28 10 Q30 6 28 2" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
        <animate attributename="d" values="M28 10 Q30 6 28 2;M28 10 Q26 6 28 2;M28 10 Q30 6 28 2" dur="2.5s" repeatcount="indefinite" />
       </path> <path d="M36 8 Q38 4 36 0" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
        <animate attributename="d" values="M36 8 Q38 4 36 0;M36 8 Q34 4 36 0;M36 8 Q38 4 36 0" dur="1.8s" repeatcount="indefinite" />
       </path> <!-- Cup body --> <path d="M8 20 L8 48 Q8 56 16 56 L40 56 Q48 56 48 48 L48 20 Z" fill="#8B5A2B" /> <!-- Coffee inside --> <path d="M12 24 L12 46 Q12 52 18 52 L38 52 Q44 52 44 46 L44 24 Z" fill="#5D3A1A" /> <!-- Cup handle --> <path d="M48 26 Q60 26 60 38 Q60 50 48 50" stroke="#8B5A2B" stroke-width="5" fill="none" stroke-linecap="round" /> <!-- Plate/Saucer --> <ellipse cx="28" cy="60" rx="26" ry="4" fill="#D4A574" />
      </svg>
      <div>
       <h1 id="platform-title" class="font-display text-2xl text-amber-900">João Café - Provas</h1>
       <p class="text-sm text-stone-500">Banco de Questões</p>
      </div>
     </div><button id="btn-add-question" onclick="openAddModal()" class="btn-primary bg-amber-700 hover:bg-amber-800 text-white px-5 py-2.5 rounded-lg font-medium flex items-center gap-2">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
      </svg><span>Adicionar Questão</span> </button>
    </div>
   </header><!-- Main Content -->
   <main class="flex-1 max-w-6xl mx-auto w-full px-4 py-6"><!-- Search & Filter Section -->
    <div class="bg-white rounded-xl shadow-sm border border-amber-100 p-4 mb-6">
     <div class="flex flex-col md:flex-row gap-4"><!-- Search Input -->
      <div class="flex-1 relative">
       <svg class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
       </svg><input type="text" id="search-input" placeholder="Buscar questões..." class="w-full pl-10 pr-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" oninput="filterQuestions()">
      </div><!-- Category Filter -->
      <div class="relative"><select id="filter-category" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]"> <option value="">Todas as Categorias</option> </select>
       <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
       </svg>
      </div><!-- Subject Filter -->
      <div class="relative"><select id="filter-subject" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]"> <option value="">Todos os Assuntos</option> </select>
       <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
       </svg>
      </div><!-- Question Type Filter -->
      <div class="relative"><select id="filter-type" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]"> <option value="">Todos os Tipos</option> <option value="Objetiva">Objetiva</option> <option value="Discursiva">Discursiva</option> <option value="Adaptada">Adaptada</option> </select>
       <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
       </svg>
      </div>
     </div><!-- Stats Bar -->
     <div class="mt-4 pt-4 border-t border-amber-100 flex items-center justify-between text-sm text-stone-500"><span id="results-count">0 questões encontradas</span> <button onclick="clearFilters()" class="text-amber-700 hover:text-amber-900 font-medium flex items-center gap-1">
       <svg class="w-4 h-4" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15" />
       </svg> Limpar Filtros </button>
     </div>
    </div><!-- Questions Grid -->
    <div id="questions-container" class="grid gap-4"><!-- Questions will be rendered here -->
    </div><!-- Empty State -->
    <div id="empty-state" class="hidden text-center py-16">
     <svg viewbox="0 0 64 64" class="w-24 h-24 mx-auto mb-4 opacity-40" fill="none"><path d="M8 20 L8 48 Q8 56 16 56 L40 56 Q48 56 48 48 L48 20 Z" fill="#8B5A2B" /> <path d="M12 24 L12 46 Q12 52 18 52 L38 52 Q44 52 44 46 L44 24 Z" fill="#5D3A1A" /> <path d="M48 26 Q60 26 60 38 Q60 50 48 50" stroke="#8B5A2B" stroke-width="5" fill="none" stroke-linecap="round" /> <ellipse cx="28" cy="60" rx="26" ry="4" fill="#D4A574" />
     </svg>
     <h3 class="font-display text-xl text-stone-600 mb-2">Nenhuma questão cadastrada</h3>
     <p class="text-stone-500 mb-4">Comece adicionando sua primeira questão ao banco</p><button onclick="openAddModal()" class="btn-primary bg-amber-700 hover:bg-amber-800 text-white px-6 py-2.5 rounded-lg font-medium inline-flex items-center gap-2">
      <svg class="w-5 h-5" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4" />
      </svg> Adicionar Primeira Questão </button>
    </div><!-- No Results State -->
    <div id="no-results-state" class="hidden text-center py-16">
     <svg class="w-16 h-16 mx-auto mb-4 text-stone-300" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
     </svg>
     <h3 class="font-display text-xl text-stone-600 mb-2">Nenhum resultado encontrado</h3>
     <p class="text-stone-500">Tente ajustar seus filtros ou termos de busca</p>
    </div>
   </main><!-- Footer -->
   <footer class="bg-white border-t border-amber-200 py-4 mt-auto">
    <div class="max-w-6xl mx-auto px-4 text-center text-sm text-stone-500">
     <p>☕ João Café - Provas • Organize suas questões com sabor</p>
    </div>
   </footer>
  </div><!-- Add/Edit Question Modal -->
  <div id="question-modal" class="hidden fixed inset-0 z-50">
   <div class="modal-backdrop absolute inset-0 bg-black/50" onclick="closeModal()"></div>
   <div class="absolute inset-4 md:inset-auto md:top-1/2 md:left-1/2 md:-translate-x-1/2 md:-translate-y-1/2 md:w-full md:max-w-2xl md:max-h-[90%] overflow-auto">
    <div class="modal-content bg-white rounded-2xl shadow-2xl overflow-hidden"><!-- Modal Header -->
     <div class="bg-amber-700 text-white px-6 py-4 flex items-center justify-between">
      <h2 id="modal-title" class="font-display text-xl">Adicionar Questão</h2><button onclick="closeModal()" class="p-1 hover:bg-amber-600 rounded-lg transition-colors">
       <svg class="w-6 h-6" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
       </svg></button>
     </div><!-- Modal Body -->
     <form id="question-form" class="p-6 space-y-5" onsubmit="handleSubmitQuestion(event)"><input type="hidden" id="edit-id" value=""> <!-- Question Text -->
      <div><label class="block text-sm font-medium text-stone-700 mb-2"> Texto da Questão <span class="text-red-500">*</span> </label> <textarea id="question-text" rows="8" required class="w-full px-4 py-3 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all resize-y" placeholder="Cole ou digite o texto completo da questão aqui..."></textarea>
       <p class="mt-1 text-xs text-stone-500">Você pode colar texto com formatação diretamente</p>
      </div><!-- Category -->
      <div><label class="block text-sm font-medium text-stone-700 mb-2"> Categoria <span class="text-red-500">*</span> </label>
       <div class="relative"><input type="text" id="question-category" required list="category-list" class="w-full px-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" placeholder="Ex: Matemática, Português, História..."> <datalist id="category-list"></datalist>
       </div>
       <p class="mt-1 text-xs text-stone-500">Digite uma nova categoria ou selecione uma existente</p>
      </div><!-- Subject -->
      <div><label class="block text-sm font-medium text-stone-700 mb-2"> Assunto/Objeto de Conhecimento <span class="text-red-500">*</span> </label>
       <div class="relative"><input type="text" id="question-subject" required list="subject-list" class="w-full px-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" placeholder="Ex: Equações do 2º grau, Interpretação de texto..."> <datalist id="subject-list"></datalist>
       </div>
       <p class="mt-1 text-xs text-stone-500">Digite um novo assunto ou selecione um existente</p>
      </div><!-- Question Type -->
      <div><label class="block text-sm font-medium text-stone-700 mb-2"> Tipo de Questão <span class="text-red-500">*</span> </label>
       <div class="flex gap-3">
        <label class="flex items-center gap-2 cursor-pointer"> <input type="radio" id="type-objetiva" name="question-type" value="Objetiva" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500"> <span class="text-sm text-stone-700">Objetiva</span> </label> <label class="flex items-center gap-2 cursor-pointer"> <input type="radio" id="type-discursiva" name="question-type" value="Discursiva" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500"> <span class="text-sm text-stone-700">Discursiva</span> </label> <label class="flex items-center gap-2 cursor-pointer"> <input type="radio" id="type-adaptada" name="question-type" value="Adaptada" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500"> <span class="text-sm text-stone-700">Adaptada</span> </label>
       </div>
      </div><!-- Image URL -->
      <div><label class="block text-sm font-medium text-stone-700 mb-2"> Imagem da Questão (Opcional) </label>
       <div class="space-y-3"><input type="url" id="question-image-url" class="w-full px-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" placeholder="Cole a URL completa da imagem (ex: https://exemplo.com/imagem.jpg)">
        <p class="text-xs text-stone-500">Formatos aceitos: JPG, PNG, GIF. Máximo 5MB. Use apenas URLs públicas.</p><!-- Image Preview -->
        <div id="image-preview-container" class="hidden">
         <div class="relative inline-block"><img id="image-preview" src="" alt="Preview" class="max-w-full h-auto rounded-lg border border-amber-200" style="max-height: 200px;"> <button type="button" onclick="removeImagePreview()" class="absolute top-2 right-2 bg-red-600 hover:bg-red-700 text-white rounded-full w-7 h-7 flex items-center justify-center transition-colors">
           <svg class="w-4 h-4" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
           </svg></button>
         </div>
        </div>
       </div>
      </div><!-- Submit Button -->
      <div class="flex gap-3 pt-4"><button type="button" onclick="closeModal()" class="flex-1 px-4 py-2.5 border border-amber-200 text-stone-700 rounded-lg font-medium hover:bg-amber-50 transition-colors"> Cancelar </button> <button type="submit" id="submit-btn" class="flex-1 btn-primary bg-amber-700 hover:bg-amber-800 text-white px-4 py-2.5 rounded-lg font-medium flex items-center justify-center gap-2"> <span id="submit-text">Salvar Questão</span>
        <svg id="submit-spinner" class="hidden w-5 h-5 animate-spin" fill="none" viewbox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle> <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z" />
        </svg></button>
      </div>
     </form>
    </div>
   </div>
  </div><!-- Delete Confirmation Modal -->
  <div id="delete-modal" class="hidden fixed inset-0 z-50">
   <div class="modal-backdrop absolute inset-0 bg-black/50" onclick="closeDeleteModal()"></div>
   <div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 w-full max-w-md">
    <div class="modal-content bg-white rounded-2xl shadow-2xl overflow-hidden mx-4">
     <div class="p-6 text-center">
      <div class="w-16 h-16 mx-auto mb-4 bg-red-100 rounded-full flex items-center justify-center">
       <svg class="w-8 h-8 text-red-600" fill="none" stroke="currentColor" viewbox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
       </svg>
      </div>
      <h3 class="font-display text-xl text-stone-800 mb-2">Excluir Questão?</h3>
      <p class="text-stone-600 mb-6">Esta ação não pode ser desfeita. A questão será removida permanentemente.</p>
      <div class="flex gap-3"><button onclick="closeDeleteModal()" class="flex-1 px-4 py-2.5 border border-stone-300 text-stone-700 rounded-lg font-medium hover:bg-stone-50 transition-colors"> Cancelar </button> <button onclick="confirmDelete()" id="confirm-delete-btn" class="flex-1 bg-red-600 hover:bg-red-700 text-white px-4 py-2.5 rounded-lg font-medium transition-colors flex items-center justify-center gap-2"> <span id="delete-text">Excluir</span>
        <svg id="delete-spinner" class="hidden w-5 h-5 animate-spin" fill="none" viewbox="0 0 24 24"><circle class="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" stroke-width="4"></circle> <path class="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z" />
        </svg></button>
      </div>
     </div>
    </div>
   </div>
  </div><!-- Toast Container -->
  <div id="toast-container" class="fixed bottom-4 right-4 z-50 space-y-2"></div>
  <script>
    // ============ State Management ============
    let allQuestions = [];
    let filteredQuestions = [];
    let categories = new Set();
    let subjects = new Set();
    let deleteTargetId = null;

    const defaultConfig = {
      platform_title: 'João Café - Provas',
      add_button_text: 'Adicionar Questão',
      search_placeholder: 'Buscar questões...',
      background_color: '#FFFBEB',
      surface_color: '#FFFFFF',
      text_color: '#292524',
      primary_action_color: '#B45309',
      secondary_action_color: '#78716C',
      font_family: 'Source Sans 3',
      font_size: 16
    };

    // ============ Element SDK Setup ============
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange: async (config) => {
          const cfg = { ...defaultConfig, ...config };
          
          // Update text content
          document.getElementById('platform-title').textContent = cfg.platform_title;
          document.querySelector('#btn-add-question span').textContent = cfg.add_button_text;
          document.getElementById('search-input').placeholder = cfg.search_placeholder;
          
          // Update colors
          document.body.style.backgroundColor = cfg.background_color;
          document.querySelectorAll('.bg-white').forEach(el => {
            el.style.backgroundColor = cfg.surface_color;
          });
          document.body.style.color = cfg.text_color;
          
          // Update primary action buttons
          document.querySelectorAll('.btn-primary').forEach(btn => {
            btn.style.backgroundColor = cfg.primary_action_color;
          });
          
          // Update fonts
          const fontStack = `${cfg.font_family}, 'Source Sans 3', sans-serif`;
          document.body.style.fontFamily = fontStack;
          
          const baseSize = cfg.font_size;
          document.getElementById('platform-title').style.fontSize = `${baseSize * 1.5}px`;
        },
        mapToCapabilities: (config) => {
          const cfg = { ...defaultConfig, ...config };
          return {
            recolorables: [
              {
                get: () => cfg.background_color,
                set: (v) => window.elementSdk.setConfig({ background_color: v })
              },
              {
                get: () => cfg.surface_color,
                set: (v) => window.elementSdk.setConfig({ surface_color: v })
              },
              {
                get: () => cfg.text_color,
                set: (v) => window.elementSdk.setConfig({ text_color: v })
              },
              {
                get: () => cfg.primary_action_color,
                set: (v) => window.elementSdk.setConfig({ primary_action_color: v })
              },
              {
                get: () => cfg.secondary_action_color,
                set: (v) => window.elementSdk.setConfig({ secondary_action_color: v })
              }
            ],
            borderables: [],
            fontEditable: {
              get: () => cfg.font_family,
              set: (v) => window.elementSdk.setConfig({ font_family: v })
            },
            fontSizeable: {
              get: () => cfg.font_size,
              set: (v) => window.elementSdk.setConfig({ font_size: v })
            }
          };
        },
        mapToEditPanelValues: (config) => {
          const cfg = { ...defaultConfig, ...config };
          return new Map([
            ['platform_title', cfg.platform_title],
            ['add_button_text', cfg.add_button_text],
            ['search_placeholder', cfg.search_placeholder]
          ]);
        }
      });
    }

    // ============ Data SDK Setup ============
    const dataHandler = {
      onDataChanged(data) {
        allQuestions = data || [];
        
        // Rebuild categories and subjects sets
        categories.clear();
        subjects.clear();
        allQuestions.forEach(q => {
          if (q.category) categories.add(q.category);
          if (q.subject) subjects.add(q.subject);
        });
        
        updateFilterDropdowns();
        filterQuestions();
      }
    };

    async function initDataSdk() {
      if (window.dataSdk) {
        const result = await window.dataSdk.init(dataHandler);
        if (!result.isOk) {
          showToast('Erro ao conectar com o banco de dados', 'error');
        }
      }
    }

    initDataSdk();

    // ============ UI Functions ============
    function updateFilterDropdowns() {
      const categorySelect = document.getElementById('filter-category');
      const subjectSelect = document.getElementById('filter-subject');
      const categoryList = document.getElementById('category-list');
      const subjectList = document.getElementById('subject-list');
      
      // Update filter dropdowns
      const currentCategory = categorySelect.value;
      const currentSubject = subjectSelect.value;
      
      categorySelect.innerHTML = '<option value="">Todas as Categorias</option>';
      subjectSelect.innerHTML = '<option value="">Todos os Assuntos</option>';
      
      Array.from(categories).sort().forEach(cat => {
        categorySelect.innerHTML += `<option value="${escapeHtml(cat)}">${escapeHtml(cat)}</option>`;
      });
      
      Array.from(subjects).sort().forEach(sub => {
        subjectSelect.innerHTML += `<option value="${escapeHtml(sub)}">${escapeHtml(sub)}</option>`;
      });
      
      categorySelect.value = currentCategory;
      subjectSelect.value = currentSubject;
      
      // Update datalists for modal inputs
      categoryList.innerHTML = Array.from(categories).sort().map(c => 
        `<option value="${escapeHtml(c)}">`
      ).join('');
      
      subjectList.innerHTML = Array.from(subjects).sort().map(s => 
        `<option value="${escapeHtml(s)}">`
      ).join('');
    }

    function filterQuestions() {
      const searchTerm = document.getElementById('search-input').value.toLowerCase().trim();
      const categoryFilter = document.getElementById('filter-category').value;
      const subjectFilter = document.getElementById('filter-subject').value;
      const typeFilter = document.getElementById('filter-type').value;
      
      filteredQuestions = allQuestions.filter(q => {
        const matchesSearch = !searchTerm || 
          q.question_text.toLowerCase().includes(searchTerm) ||
          q.category.toLowerCase().includes(searchTerm) ||
          q.subject.toLowerCase().includes(searchTerm) ||
          q.question_type.toLowerCase().includes(searchTerm);
        
        const matchesCategory = !categoryFilter || q.category === categoryFilter;
        const matchesSubject = !subjectFilter || q.subject === subjectFilter;
        const matchesType = !typeFilter || q.question_type === typeFilter;
        
        return matchesSearch && matchesCategory && matchesSubject && matchesType;
      });
      
      renderQuestions();
    }

    function renderQuestions() {
      const container = document.getElementById('questions-container');
      const emptyState = document.getElementById('empty-state');
      const noResultsState = document.getElementById('no-results-state');
      const resultsCount = document.getElementById('results-count');
      
      // Update count
      resultsCount.textContent = `${filteredQuestions.length} questão(ões) encontrada(s)`;
      
      // Handle empty states
      if (allQuestions.length === 0) {
        container.innerHTML = '';
        emptyState.classList.remove('hidden');
        noResultsState.classList.add('hidden');
        return;
      }
      
      emptyState.classList.add('hidden');
      
      if (filteredQuestions.length === 0) {
        container.innerHTML = '';
        noResultsState.classList.remove('hidden');
        return;
      }
      
      noResultsState.classList.add('hidden');
      
      // Render questions with efficient DOM updates
      const existingCards = new Map();
      container.querySelectorAll('.question-card').forEach(card => {
        existingCards.set(card.dataset.id, card);
      });
      
      const fragment = document.createDocumentFragment();
      const newIds = new Set();
      
      filteredQuestions.forEach(q => {
        newIds.add(q.__backendId);
        
        if (existingCards.has(q.__backendId)) {
          const card = existingCards.get(q.__backendId);
          updateQuestionCard(card, q);
          fragment.appendChild(card);
        } else {
          fragment.appendChild(createQuestionCard(q));
        }
      });
      
      // Remove cards that are no longer visible
      existingCards.forEach((card, id) => {
        if (!newIds.has(id)) {
          card.remove();
        }
      });
      
      container.innerHTML = '';
      container.appendChild(fragment);
    }

    function createQuestionCard(question) {
      const card = document.createElement('div');
      card.className = 'question-card bg-white rounded-xl shadow-sm border border-amber-100 p-5';
      card.dataset.id = question.__backendId;
      
      let imageHtml = '';
      if (question.question_image) {
        imageHtml = `
          <div class="mb-4 rounded-lg overflow-hidden border border-amber-100">
            <img src="${question.question_image}" alt="Imagem da questão" class="w-full h-auto max-h-64 object-contain bg-stone-50" loading="lazy" onerror="this.parentElement.style.display='none'">
          </div>
        `;
      }
      
      card.innerHTML = `
        <div class="flex items-start justify-between gap-4 mb-3">
          <div class="flex flex-wrap gap-2">
            <span class="tag inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-amber-100 text-amber-800">
              ${escapeHtml(question.category)}
            </span>
            <span class="tag inline-flex items-center px-3 py-1 rounded-full text-sm font-medium bg-stone-100 text-stone-700">
              ${escapeHtml(question.subject)}
            </span>
            <span class="tag inline-flex items-center px-3 py-1 rounded-full text-sm font-medium ${question.question_type === 'Objetiva' ? 'bg-blue-100 text-blue-800' : question.question_type === 'Discursiva' ? 'bg-purple-100 text-purple-800' : 'bg-rose-100 text-rose-800'}">
              ${question.question_type === 'Objetiva' ? '📋 Objetiva' : question.question_type === 'Discursiva' ? '✍️ Discursiva' : '🎯 Adaptada'}
            </span>
          </div>
          <div class="flex items-center gap-1 shrink-0">
            <button onclick="editQuestion('${question.__backendId}')" 
              class="p-2 text-stone-400 hover:text-amber-700 hover:bg-amber-50 rounded-lg transition-colors" title="Editar">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"/>
              </svg>
            </button>
            <button onclick="openDeleteModal('${question.__backendId}')" 
              class="p-2 text-stone-400 hover:text-red-600 hover:bg-red-50 rounded-lg transition-colors" title="Excluir">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
              </svg>
            </button>
          </div>
        </div>
        ${imageHtml}
        <div class="question-text text-stone-700 whitespace-pre-wrap break-words">${escapeHtml(question.question_text)}</div>
        <div class="mt-4 pt-3 border-t border-amber-50 text-xs text-stone-400">
          Adicionada em ${formatDate(question.created_at)}
        </div>
      `;
      
      return card;
    }

    function updateQuestionCard(card, question) {
      const categoryTag = card.querySelector('.tag:first-child');
      const subjectTag = card.querySelector('.tag:last-of-type');
      const textEl = card.querySelector('.question-text');
      const dateEl = card.querySelector('.border-t');
      
      if (categoryTag) categoryTag.textContent = question.category;
      if (subjectTag) subjectTag.textContent = question.subject;
      if (textEl) textEl.textContent = question.question_text;
      if (dateEl) dateEl.innerHTML = `Adicionada em ${formatDate(question.created_at)}`;
    }

    // ============ Modal Functions ============
    function openAddModal() {
      document.getElementById('modal-title').textContent = 'Adicionar Questão';
      document.getElementById('submit-text').textContent = 'Salvar Questão';
      document.getElementById('edit-id').value = '';
      document.getElementById('question-form').reset();
      // Reset radio buttons
      document.getElementById('type-objetiva').checked = false;
      document.getElementById('type-discursiva').checked = false;
      document.getElementById('question-modal').classList.remove('hidden');
      document.body.style.overflow = 'hidden';
    }

    function editQuestion(id) {
      const question = allQuestions.find(q => q.__backendId === id);
      if (!question) return;
      
      document.getElementById('modal-title').textContent = 'Editar Questão';
      document.getElementById('submit-text').textContent = 'Atualizar Questão';
      document.getElementById('edit-id').value = id;
      document.getElementById('question-text').value = question.question_text;
      document.getElementById('question-category').value = question.category;
      document.getElementById('question-subject').value = question.subject;
      
      // Set radio button for question type
      if (question.question_type === 'Objetiva') {
        document.getElementById('type-objetiva').checked = true;
      } else if (question.question_type === 'Discursiva') {
        document.getElementById('type-discursiva').checked = true;
      } else if (question.question_type === 'Adaptada') {
        document.getElementById('type-adaptada').checked = true;
      }
      
      // Show image preview if exists
      if (question.question_image) {
        showImagePreview(question.question_image);
      } else {
        removeImagePreview();
      }
      
      document.getElementById('question-modal').classList.remove('hidden');
      document.body.style.overflow = 'hidden';
    }

    function closeModal() {
      document.getElementById('question-modal').classList.add('hidden');
      document.body.style.overflow = '';
    }

    function openDeleteModal(id) {
      deleteTargetId = id;
      document.getElementById('delete-modal').classList.remove('hidden');
      document.body.style.overflow = 'hidden';
    }

    function closeDeleteModal() {
      deleteTargetId = null;
      document.getElementById('delete-modal').classList.add('hidden');
      document.body.style.overflow = '';
    }

    // ============ Form Handling ============
    async function handleSubmitQuestion(e) {
      e.preventDefault();
      
      if (!window.dataSdk) {
        showToast('SDK não disponível', 'error');
        return;
      }
      
      const editId = document.getElementById('edit-id').value;
      const questionText = document.getElementById('question-text').value.trim();
      const category = document.getElementById('question-category').value.trim();
      const subject = document.getElementById('question-subject').value.trim();
      const questionType = document.querySelector('input[name="question-type"]:checked')?.value;
      const imageBase64 = document.getElementById('question-image-file').dataset.imageBase64 || '';
      
      if (!questionText || !category || !subject || !questionType) {
        showToast('Por favor, preencha todos os campos obrigatórios', 'error');
        return;
      }
      
      // Check limit for new questions
      if (!editId && allQuestions.length >= 999) {
        showToast('Limite máximo de 999 questões atingido', 'error');
        return;
      }
      
      // Show loading state
      const submitBtn = document.getElementById('submit-btn');
      const submitText = document.getElementById('submit-text');
      const submitSpinner = document.getElementById('submit-spinner');
      submitBtn.disabled = true;
      submitText.textContent = editId ? 'Atualizando...' : 'Salvando...';
      submitSpinner.classList.remove('hidden');
      
      let result;
      
      if (editId) {
        const question = allQuestions.find(q => q.__backendId === editId);
        if (question) {
          result = await window.dataSdk.update({
            ...question,
            question_text: questionText,
            category: category,
            subject: subject,
            question_type: questionType,
            question_image: imageBase64
          });
        }
      } else {
        result = await window.dataSdk.create({
          question_text: questionText,
          category: category,
          subject: subject,
          question_type: questionType,
          question_image: imageBase64,
          created_at: new Date().toISOString()
        });
      }
      
      // Reset loading state
      submitBtn.disabled = false;
      submitText.textContent = editId ? 'Atualizar Questão' : 'Salvar Questão';
      submitSpinner.classList.add('hidden');
      
      if (result && result.isOk) {
        closeModal();
        showToast(editId ? 'Questão atualizada com sucesso!' : 'Questão adicionada com sucesso!', 'success');
      } else {
        showToast('Erro ao salvar questão. Tente novamente.', 'error');
      }
    }

    async function confirmDelete() {
      if (!deleteTargetId || !window.dataSdk) return;
      
      const question = allQuestions.find(q => q.__backendId === deleteTargetId);
      if (!question) return;
      
      // Show loading state
      const deleteBtn = document.getElementById('confirm-delete-btn');
      const deleteText = document.getElementById('delete-text');
      const deleteSpinner = document.getElementById('delete-spinner');
      deleteBtn.disabled = true;
      deleteText.textContent = 'Excluindo...';
      deleteSpinner.classList.remove('hidden');
      
      const result = await window.dataSdk.delete(question);
      
      // Reset loading state
      deleteBtn.disabled = false;
      deleteText.textContent = 'Excluir';
      deleteSpinner.classList.add('hidden');
      
      if (result.isOk) {
        closeDeleteModal();
        showToast('Questão excluída com sucesso!', 'success');
      } else {
        showToast('Erro ao excluir questão. Tente novamente.', 'error');
      }
    }

    function clearFilters() {
      document.getElementById('search-input').value = '';
      document.getElementById('filter-category').value = '';
      document.getElementById('filter-subject').value = '';
      filterQuestions();
    }

    // ============ Utility Functions ============
    function escapeHtml(str) {
      if (!str) return '';
      const div = document.createElement('div');
      div.textContent = str;
      return div.innerHTML;
    }

    function formatDate(isoString) {
      if (!isoString) return '';
      const date = new Date(isoString);
      return date.toLocaleDateString('pt-BR', {
        day: '2-digit',
        month: '2-digit',
        year: 'numeric',
        hour: '2-digit',
        minute: '2-digit'
      });
    }

    function showToast(message, type = 'info') {
      const container = document.getElementById('toast-container');
      const toast = document.createElement('div');
      
      const bgColor = type === 'success' ? 'bg-green-600' : 
                      type === 'error' ? 'bg-red-600' : 'bg-stone-700';
      
      toast.className = `toast ${bgColor} text-white px-4 py-3 rounded-lg shadow-lg flex items-center gap-2`;
      
      const icon = type === 'success' 
        ? '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"/></svg>'
        : type === 'error'
        ? '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/></svg>'
        : '<svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>';
      
      toast.innerHTML = `${icon}<span>${escapeHtml(message)}</span>`;
      container.appendChild(toast);
      
      setTimeout(() => {
        toast.remove();
      }, 3000);
    }

    function isValidImageUrl(url) {
      try {
        const urlObj = new URL(url);
        return urlObj.protocol === 'http:' || urlObj.protocol === 'https:';
      } catch (e) {
        return false;
      }
    }

    function handleImageFileUpload(event) {
      const file = event.target.files[0];
      if (!file) return;
      
      // Validate file size (5MB max)
      const maxSize = 5 * 1024 * 1024;
      if (file.size > maxSize) {
        showToast('Arquivo muito grande. Máximo 5MB.', 'error');
        document.getElementById('question-image-file').value = '';
        return;
      }
      
      // Validate file type
      if (!file.type.startsWith('image/')) {
        showToast('Por favor, selecione um arquivo de imagem válido.', 'error');
        document.getElementById('question-image-file').value = '';
        return;
      }
      
      // Convert to base64
      const reader = new FileReader();
      reader.onload = function(e) {
        const base64String = e.target.result;
        document.getElementById('question-image-file').dataset.imageBase64 = base64String;
        showImagePreview(base64String);
        showToast('Imagem carregada com sucesso!', 'success');
      };
      reader.onerror = function() {
        showToast('Erro ao ler o arquivo. Tente novamente.', 'error');
        document.getElementById('question-image-file').value = '';
      };
      reader.readAsDataURL(file);
    }

    function showImagePreview(dataUrl) {
      const previewContainer = document.getElementById('image-preview-container');
      const previewImg = document.getElementById('image-preview');
      previewImg.src = dataUrl;
      previewContainer.classList.remove('hidden');
    }

    function removeImagePreview() {
      document.getElementById('image-preview-container').classList.add('hidden');
      document.getElementById('image-preview').src = '';
      document.getElementById('question-image-file').value = '';
      document.getElementById('question-image-file').dataset.imageBase64 = '';
    }

    // Initial render
    filterQuestions();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d836825a3d06d6a',t:'MTc3MjgyMTU2Ni4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>
