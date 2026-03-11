<!doctype html>
<html lang="pt-BR" class="h-full">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>João Café - Provas</title>

    <!-- Tailwind CDN correto -->
    <script src="https://ss.com</script>
    <script>
      // Sanity check: ajuda a diagnosticar caso o CDN falhe
      if (typeof tailwind === 'undefined') {
        console.error('Tailwind NÃO carregou. Verifique o CDN/Network.');
      } else {
        console.log('Tailwind carregado ✓');
      }
    </script>

    <!-- SDKs da plataforma (ajuste o caminho se necessário) -->
    /_sdk/element_sdk.js</script>
    /_sdk/data_sdk.js</script>

    <!-- Fonts -->
    https://fonts.googleapis.com/css2?family=Playfair+Display:wght@600;700&family=Source+Sans+3:wght@400;500;600&display=swap

    <style>
      * { box-sizing: border-box; }
      html, body { height: 100%; margin: 0; padding: 0; }
      .font-display { font-family: 'Playfair Display', serif; }
      .font-body { font-family: 'Source Sans 3', sans-serif; }

      .question-card { transition: all 0.2s ease; }
      .question-card:hover { transform: translateY(-2px); box-shadow: 0 8px 25px rgba(139, 90, 43, 0.15); }

      .tag { transition: all 0.15s ease; }
      .tag:hover { transform: scale(1.05); }

      .btn-primary { transition: all 0.2s ease; }
      .btn-primary:hover { transform: translateY(-1px); box-shadow: 0 4px 12px rgba(139, 90, 43, 0.3); }

      .modal-backdrop { animation: fadeIn 0.2s ease; }
      @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

      .modal-content { animation: slideUp 0.3s ease; }
      @keyframes slideUp { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

      .toast { animation: slideIn 0.3s ease, fadeOut 0.3s ease 2.7s forwards; }
      @keyframes slideIn { from { transform: translateX(100%); opacity: 0; } to { transform: translateX(0); opacity: 1; } }
      @keyframes fadeOut { from { opacity: 1; } to { opacity: 0; } }

      .dropdown-menu { animation: dropDown 0.2s ease; }
      @keyframes dropDown { from { opacity: 0; transform: translateY(-10px); } to { opacity: 1; transform: translateY(0); } }
    </style>

    <!-- Ícones (Lucide) -->
    https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js</script>
  </head>

  <body class="h-full font-body bg-amber-50 text-stone-800 overflow-auto">
    <div id="app" class="min-h-full w-full flex flex-col">
      <!-- Header -->
      <header class="bg-white border-b border-amber-200 shadow-sm sticky top-0 z-40">
        <div class="max-w-6xl mx-auto px-4 py-4 flex items-center justify-between">
          <div class="flex items-center gap-3">
            <!-- Coffee Cup SVG Logo -->
            <svg viewBox="0 0 64 64" class="w-12 h-12" fill="none">
              <!-- Steam lines -->
              <path d="M20 8 Q22 4 20 0" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
                <animate attributeName="d" values="M20 8 Q22 4 20 0;M20 8 Q18 4 20 0;M20 8 Q22 4 20 0" dur="2s" repeatCount="indefinite"/>
              </path>
              <path d="M28 10 Q30 6 28 2" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
                <animate attributeName="d" values="M28 10 Q30 6 28 2;M28 10 Q26 6 28 2;M28 10 Q30 6 28 2" dur="2.5s" repeatCount="indefinite"/>
              </path>
              <path d="M36 8 Q38 4 36 0" stroke="#8B5A2B" stroke-width="2" stroke-linecap="round" fill="none" opacity="0.6">
                <animate attributeName="d" values="M36 8 Q38 4 36 0;M36 8 Q34 4 36 0;M36 8 Q38 4 36 0" dur="1.8s" repeatCount="indefinite"/>
              </path>
              <!-- Cup body -->
              <path d="M8 20 L8 48 Q8 56 16 56 L40 56 Q48 56 48 48 L48 20 Z" fill="#8B5A2B"/>
              <!-- Coffee inside -->
              <path d="M12 24 L12 46 Q12 52 18 52 L38 52 Q44 52 44 46 L44 24 Z" fill="#5D3A1A"/>
              <!-- Cup handle -->
              <path d="M48 26 Q60 26 60 38 Q60 50 48 50" stroke="#8B5A2B" stroke-width="5" fill="none" stroke-linecap="round"/>
              <!-- Plate/Saucer -->
              <ellipse cx="28" cy="60" rx="26" ry="4" fill="#D4A574"/>
            </svg>

            <div>
              <h1 id="platform-title" class="font-display text-2xl text-amber-900">João Café - Provas</h1>
              <p class="text-sm text-stone-500">Banco de Questões</p>
            </div>
          </div>

          <button id="btn-add-question" onclick="openAddModal()" class="btn-primary bg-amber-700 hover:bg-amber-800 text-white px-5 py-2.5 rounded-lg font-medium flex items-center gap-2">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/>
            </svg>
            <span>Adicionar Questão</span>
          </button>
        </div>
      </header>

      <!-- Main Content -->
      <main class="flex-1 max-w-6xl mx-auto w-full px-4 py-6">
        <!-- Search & Filter Section -->
        <div class="bg-white rounded-xl shadow-sm border border-amber-100 p-4 mb-6">
          <div class="flex flex-col md:flex-row gap-4">
            <!-- Search Input -->
            <div class="flex-1 relative">
              <svg class="absolute left-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
              </svg>
              <input type="text" id="search-input" placeholder="Buscar questões..." class="w-full pl-10 pr-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" oninput="filterQuestions()">
            </div>

            <!-- Category Filter -->
            <div class="relative">
              <select id="filter-category" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]">
                <option value="">Todas as Categorias</option>
              </select>
              <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
              </svg>
            </div>

            <!-- Subject Filter -->
            <div class="relative">
              <select id="filter-subject" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]">
                <option value="">Todos os Assuntos</option>
              </select>
              <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
              </svg>
            </div>

            <!-- Question Type Filter -->
            <div class="relative">
              <select id="filter-type" onchange="filterQuestions()" class="appearance-none bg-white border border-amber-200 rounded-lg px-4 py-2.5 pr-10 focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none cursor-pointer min-w-[180px]">
                <option value="">Todos os Tipos</option>
                <option value="Objetiva">Objetiva</option>
                <option value="Discursiva">Discursiva</option>
                <option value="Adaptada">Adaptada</option>
              </select>
              <svg class="absolute right-3 top-1/2 -translate-y-1/2 w-5 h-5 text-stone-400 pointer-events-none" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
              </svg>
            </div>
          </div>

          <!-- Stats Bar -->
          <div class="mt-4 pt-4 border-t border-amber-100 flex items-center justify-between text-sm text-stone-500">
            <span id="results-count">0 questões encontradas</span>
            <button onclick="clearFilters()" class="text-amber-700 hover:text-amber-900 font-medium flex items-center gap-1">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/>
              </svg>
              Limpar Filtros
            </button>
          </div>
        </div>

        <!-- Questions Grid -->
        <div id="questions-container" class="grid gap-4"></div>

        <!-- Empty State -->
        <div id="empty-state" class="hidden text-center py-16">
          <svg viewBox="0 0 64 64" class="w-24 h-24 mx-auto mb-4 opacity-40" fill="none">
            <path d="M8 20 L8 48 Q8 56 16 56 L40 56 Q48 56 48 48 L48 20 Z" fill="#8B5A2B" />
            <path d="M12 24 L12 46 Q12 52 18 52 L38 52 Q44 52 44 46 L44 24 Z" fill="#5D3A1A" />
            <path d="M48 26 Q60 26 60 38 Q60 50 48 50" stroke="#8B5A2B" stroke-width="5" fill="none" stroke-linecap="round" />
            <ellipse cx="28" cy="60" rx="26" ry="4" fill="#D4A574" />
          </svg>
          <h3 class="font-display text-xl text-stone-600 mb-2">Nenhuma questão cadastrada</h3>
          <p class="text-stone-500 mb-4">Comece adicionando sua primeira questão ao banco</p>
          <button onclick="openAddModal()" class="btn-primary bg-amber-700 hover:bg-amber-800 text-white px-6 py-2.5 rounded-lg font-medium inline-flex items-center gap-2">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/>
            </svg>
            Adicionar Primeira Questão
          </button>
        </div>

        <!-- No Results State -->
        <div id="no-results-state" class="hidden text-center py-16">
          <svg class="w-16 h-16 mx-auto mb-4 text-stone-300" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
          </svg>
          <h3 class="font-display text-xl text-stone-600 mb-2">Nenhum resultado encontrado</h3>
          <p class="text-stone-500">Tente ajustar seus filtros ou termos de busca</p>
        </div>
      </main>

      <!-- Footer -->
      <footer class="bg-white border-t border-amber-200 py-4 mt-auto">
        <div class="max-w-6xl mx-auto px-4 text-center text-sm text-stone-500">
          <p>☕ João Café - Provas • Organize suas questões com sabor</p>
        </div>
      </footer>
    </div>

    <!-- Add/Edit Question Modal -->
    <div id="question-modal" class="hidden fixed inset-0 z-50">
      <div class="modal-backdrop absolute inset-0 bg-black/50" onclick="closeModal()"></div>
      <div class="absolute inset-4 md:inset-auto md:top-1/2 md:left-1/2 md:-translate-x-1/2 md:-translate-y-1/2 md:w-full md:max-w-2xl md:max-h-[90%] overflow-auto">
        <div class="modal-content bg-white rounded-2xl shadow-2xl overflow-hidden">
          <!-- Modal Header -->
          <div class="bg-amber-700 text-white px-6 py-4 flex items-center justify-between">
            <h2 id="modal-title" class="font-display text-xl">Adicionar Questão</h2>
            <button onclick="closeModal()" class="p-1 hover:bg-amber-600 rounded-lg transition-colors">
              <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
              </svg>
            </button>
          </div>

          <!-- Modal Body -->
          <form id="question-form" class="p-6 space-y-5" onsubmit="handleSubmitQuestion(event)">
            <input type="hidden" id="edit-id" value=""/>

            <!-- Question Text -->
            <div>
              <label class="block text-sm font-medium text-stone-700 mb-2">
                Texto da Questão <span class="text-red-500">*</span>
              </label>
              <textarea id="question-text" rows="8" required class="w-full px-4 py-3 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all resize-y" placeholder="Cole ou digite o texto completo da questão aqui..."></textarea>
              <p class="mt-1 text-xs text-stone-500">Você pode colar texto com formatação diretamente</p>
            </div>

            <!-- Category -->
            <div>
              <label class="block text-sm font-medium text-stone-700 mb-2">
                Categoria <span class="text-red-500">*</span>
              </label>
              <div class="relative">
                <input type="text" id="question-category" required list="category-list" class="w-full px-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" placeholder="Ex: Matemática, Português, História...">
                <datalist id="category-list"></datalist>
              </div>
              <p class="mt-1 text-xs text-stone-500">Digite uma nova categoria ou selecione uma existente</p>
            </div>

            <!-- Subject -->
            <div>
              <label class="block text-sm font-medium text-stone-700 mb-2">
                Assunto/Objeto de Conhecimento <span class="text-red-500">*</span>
              </label>
              <div class="relative">
                <input type="text" id="question-subject" required list="subject-list" class="w-full px-4 py-2.5 border border-amber-200 rounded-lg focus:ring-2 focus:ring-amber-500 focus:border-amber-500 outline-none transition-all" placeholder="Ex: Equações do 2º grau, Interpretação de texto...">
                <datalist id="subject-list"></datalist>
              </div>
              <p class="mt-1 text-xs text-stone-500">Digite um novo assunto ou selecione uma existente</p>
            </div>

            <!-- Question Type -->
            <div>
              <label class="block text-sm font-medium text-stone-700 mb-2">
                Tipo de Questão <span class="text-red-500">*</span>
              </label>
              <div class="flex gap-3">
                <label class="flex items-center gap-2 cursor-pointer">
                  <input type="radio" id="type-objetiva" name="question-type" value="Objetiva" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500">
                  <span class="text-sm text-stone-700">Objetiva</span>
                </label>
                <label class="flex items-center gap-2 cursor-pointer">
                  <input type="radio" id="type-discursiva" name="question-type" value="Discursiva" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500">
                  <span class="text-sm text-stone-700">Discursiva</span>
                </label>
                <label class="flex items-center gap-2 cursor-pointer">
                  <input type="radio" id="type-adaptada" name="question-type" value="Adaptada" required class="w-4 h-4 text-amber-600 border-amber-300 focus:ring-amber-500">
                  <span class="text-sm text-stone-700">Adaptada</span>
                </label>
              </div>
            </div>

            <!-- Image Upload -->
            <div>
              <label class="block text-sm font-medium text-stone-700 mb-2">Imagem da Questão (Opcional)</label>
              <div class="space-y-3">
                <div class="relative border-2 border-dashed border-amber-200 rounded-lg p-6 text-center hover:border-amber-400 transition-colors cursor-pointer" onclick="document.getElementById('question-image-file').click()">
                  <svg class="w-8 h-8 mx-auto mb-2 text-stone-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/>
                  </svg>
                  <p class="text-sm text-stone-700 font-medium">Clique para selecionar uma imagem</p>
                  <p class="text-xs text-stone-500 mt-1">ou arraste uma imagem aqui</p>
                  <input type="file" id="question-image-file" class="hidden" accept="image/*" onchange="handleImageFileUpload(event)">
                </div>
                <p class="text-xs text-stone-500">Formatos: JPG, PNG, GIF. Máximo 5MB.</p>

                <!-- Image Preview -->
                <div id="image-preview-container" class="hidden">
                  <div class="relative inline-block">
                    <img id="image-preview" src="" alt="Preview" class="max-w-full h-auto rounded-lg border border-amber-200" style="max-height: 200px;">
                    <button type="button" onclick="removeImagePreview()" class="absolute top-2 right-2 bg-red-600 hover:bg-red-700 text-white rounded-full w-7 h-7 flex items-center justify-center transition-colors">
