# robotics-form
forms-robotica
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Inscrição para Competição de Robótica</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        .container {
            background-color: #ffffff;
            padding: 32px;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            max-width: 800px;
            width: 100%;
        }
        .form-group {
            margin-bottom: 20px;
        }
        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #374151;
        }
        .form-input {
            width: 100%;
            padding: 12px;
            border: 1px solid #d1d5db;
            border-radius: 8px;
            font-size: 16px;
            color: #4b5563;
        }
        .form-input:focus {
            outline: none;
            border-color: #2563eb;
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.25);
        }
        .student-section {
            border: 1px dashed #9ca3af;
            padding: 24px;
            border-radius: 8px;
            margin-bottom: 24px;
            background-color: #f9fafb;
        }
        .btn {
            padding: 12px 24px;
            border-radius: 8px;
            font-weight: 600;
            cursor: pointer;
            transition: background-color 0.2s ease-in-out;
            display: inline-flex;
            align-items: center;
            justify-content: center;
        }
        .btn-primary {
            background-color: #2563eb;
            color: #ffffff;
        }
        .btn-primary:hover {
            background-color: #1d4ed8;
        }
        .btn-secondary {
            background-color: #6b7280;
            color: #ffffff;
            margin-left: 10px;
        }
        .btn-secondary:hover {
            background-color: #4b5563;
        }
        .btn-add-student {
            background-color: #10b981;
            color: #ffffff;
        }
        .btn-add-student:hover {
            background-color: #059669;
        }
        .btn-remove-student {
            background-color: #ef4444;
            color: #ffffff;
            margin-top: 16px;
        }
        .btn-remove-student:hover {
            background-color: #dc2626;
        }
        .message-box {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background-color: #ffffff;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            z-index: 1000;
            text-align: center;
            display: none; /* Hidden by default */
        }
        .message-box h3 {
            margin-bottom: 15px;
            color: #333;
        }
        .message-box button {
            background-color: #2563eb;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
        }
        .message-box button:hover {
            background-color: #1d4ed8;
        }
        .loading-spinner {
            border: 4px solid #f3f3f3;
            border-top: 4px solid #2563eb;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            vertical-align: middle;
            margin-left: 8px;
            display: none; /* Hidden by default */
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="container">
        <h2 class="text-3xl font-bold text-center text-gray-800 mb-8">Inscrição para Competição de Robótica</h2>

        <form id="roboticsForm" class="space-y-6">
            <div class="form-group">
                <label for="teamName" class="form-label">Nome da Equipe</label>
                <div class="flex items-center gap-2">
                    <input type="text" id="teamName" name="teamName" class="form-input" placeholder="Ex: Robô Voador" required>
                    <button type="button" id="generateDescriptionBtn" class="btn btn-secondary whitespace-nowrap">
                        ✨ Gerar Descrição
                        <span id="loadingSpinner" class="loading-spinner"></span>
                    </button>
                </div>
                <div id="teamDescriptionOutput" class="mt-4 p-3 bg-gray-100 rounded-md text-gray-700 hidden"></div>
            </div>

            <div id="studentsContainer">
                <div class="student-section" data-student-id="1">
                    <h3 class="text-xl font-semibold text-gray-700 mb-4">Aluno 1</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="form-group">
                            <label for="fullName_1" class="form-label">Nome Completo</label>
                            <input type="text" id="fullName_1" name="fullName_1" class="form-input" placeholder="Ex: João Silva" required>
                        </div>
                        <div class="form-group">
                            <label for="gradeClass_1" class="form-label">Série e Turma</label>
                            <input type="text" id="gradeClass_1" name="gradeClass_1" class="form-input" placeholder="Ex: 8º Ano A" required>
                        </div>
                        <div class="form-group">
                            <label for="birthYear_1" class="form-label">Ano de Nascimento</label>
                            <input type="number" id="birthYear_1" name="birthYear_1" class="form-input" placeholder="Ex: 2008" min="1900" max="2025" required>
                        </div>
                        <div class="form-group">
                            <label for="contactNumber_1" class="form-label">Número para Contato</label>
                            <input type="tel" id="contactNumber_1" name="contactNumber_1" class="form-input" placeholder="Ex: (XX) XXXXX-XXXX" pattern="^\(\d{2}\)\s\d{4,5}-\d{4}$" title="Formato: (XX) XXXXX-XXXX ou (XX) XXXX-XXXX" required>
                        </div>
                    </div>
                </div>
            </div>

            <div class="flex justify-end gap-4 mt-6">
                <button type="button" id="addStudentBtn" class="btn btn-add-student">
                    Adicionar Aluno (Máx. 6)
                </button>
                <button type="submit" class="btn btn-primary">
                    Enviar e Imprimir
                </button>
            </div>
        </form>
    </div>

    <div id="messageBox" class="message-box">
        <h3 id="messageText"></h3>
        <button onclick="document.getElementById('messageBox').style.display='none'">OK</button>
    </div>

    <script>
        const studentsContainer = document.getElementById('studentsContainer');
        const addStudentBtn = document.getElementById('addStudentBtn');
        const roboticsForm = document.getElementById('roboticsForm');
        const generateDescriptionBtn = document.getElementById('generateDescriptionBtn');
        const teamNameInput = document.getElementById('teamName');
        const teamDescriptionOutput = document.getElementById('teamDescriptionOutput');
        const loadingSpinner = document.getElementById('loadingSpinner');
        let studentCount = 1; // Começa com 1 aluno já presente

        // Função para exibir mensagens personalizadas
        function showMessage(message) {
            const messageBox = document.getElementById('messageBox');
            const messageText = document.getElementById('messageText');
            messageText.textContent = message;
            messageBox.style.display = 'block';
        }

        // Função para adicionar um novo campo de aluno
        function addStudentSection() {
            if (studentCount < 6) {
                studentCount++;
                const newStudentSection = document.createElement('div');
                newStudentSection.classList.add('student-section');
                newStudentSection.setAttribute('data-student-id', studentCount);
                newStudentSection.innerHTML = `
                    <h3 class="text-xl font-semibold text-gray-700 mb-4">Aluno ${studentCount}</h3>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                        <div class="form-group">
                            <label for="fullName_${studentCount}" class="form-label">Nome Completo</label>
                            <input type="text" id="fullName_${studentCount}" name="fullName_${studentCount}" class="form-input" placeholder="Ex: Maria Souza" required>
                        </div>
                        <div class="form-group">
                            <label for="gradeClass_${studentCount}" class="form-label">Série e Turma</label>
                            <input type="text" id="gradeClass_${studentCount}" name="gradeClass_${studentCount}" class="form-input" placeholder="Ex: 9º Ano B" required>
                        </div>
                        <div class="form-group">
                            <label for="birthYear_${studentCount}" class="form-label">Ano de Nascimento</label>
                            <input type="number" id="birthYear_${studentCount}" name="birthYear_${studentCount}" class="form-input" placeholder="Ex: 2007" min="1900" max="2025" required>
                        </div>
                        <div class="form-group">
                            <label for="contactNumber_${studentCount}" class="form-label">Número para Contato</label>
                            <input type="tel" id="contactNumber_${studentCount}" name="contactNumber_${studentCount}" class="form-input" placeholder="Ex: (XX) XXXXX-XXXX" pattern="^\(\d{2}\)\s\d{4,5}-\d{4}$" title="Formato: (XX) XXXXX-XXXX ou (XX) XXXX-XXXX" required>
                        </div>
                    </div>
                    <button type="button" class="btn btn-remove-student" onclick="removeStudentSection(this)">Remover Aluno</button>
                `;
                studentsContainer.appendChild(newStudentSection);

                // Desabilita o botão se atingir o limite
                if (studentCount === 6) {
                    addStudentBtn.disabled = true;
                    addStudentBtn.classList.add('opacity-50', 'cursor-not-allowed');
                }
            } else {
                showMessage("Você atingiu o limite máximo de 6 alunos.");
            }
        }

        // Função para remover um campo de aluno
        function removeStudentSection(button) {
            const studentSectionToRemove = button.closest('.student-section');
            studentSectionToRemove.remove();
            studentCount--;

            // Reabilita o botão se estiver abaixo do limite
            if (studentCount < 6) {
                addStudentBtn.disabled = false;
                addStudentBtn.classList.remove('opacity-50', 'cursor-not-allowed');
            }

            // Atualiza os números dos alunos restantes
            const remainingStudentSections = studentsContainer.querySelectorAll('.student-section');
            remainingStudentSections.forEach((section, index) => {
                const studentId = index + 1;
                section.setAttribute('data-student-id', studentId);
                section.querySelector('h3').textContent = `Aluno ${studentId}`;
                section.querySelectorAll('input').forEach(input => {
                    const oldName = input.name;
                    const oldId = input.id;
                    input.name = oldName.replace(/_\d+$/, `_${studentId}`);
                    input.id = oldId.replace(/_\d+$/, `_${studentId}`);
                    input.previousElementSibling.setAttribute('for', input.id);
                });
            });
        }

        // Função para gerar o conteúdo HTML para impressão
        function generatePrintableContent(formData) {
            let studentsHtml = '';
            formData.students.forEach((student, index) => {
                studentsHtml += `
                    <div style="margin-bottom: 20px; padding-bottom: 10px; border-bottom: 1px solid #ccc;">
                        <h3 style="font-size: 1.2em; margin-bottom: 10px;">Aluno ${index + 1}</h3>
                        <p><strong>Nome Completo:</strong> ${student.fullName}</p>
                        <p><strong>Série e Turma:</strong> ${student.gradeClass}</p>
                        <p><strong>Ano de Nascimento:</strong> ${student.birthYear}</p>
                        <p><strong>Número para Contato:</strong> ${student.contactNumber}</p>
                    </div>
                `;
            });

            return `
                <!DOCTYPE html>
                <html lang="pt-BR">
                <head>
                    <meta charset="UTF-8">
                    <meta name="viewport" content="width=device-width, initial-scale=1.0">
                    <title>Dados de Inscrição da Equipe ${formData.teamName}</title>
                    <style>
                        body { font-family: 'Inter', sans-serif; margin: 20px; color: #333; }
                        h1 { color: #2563eb; text-align: center; margin-bottom: 30px; }
                        h2 { color: #4b5563; margin-bottom: 20px; }
                        p { margin-bottom: 8px; }
                        strong { font-weight: 600; }
                        @media print {
                            body { margin: 0; padding: 0; }
                            .no-print { display: none; }
                        }
                    </style>
                </head>
                <body>
                    <h1>Inscrição para Competição de Robótica</h1>
                    <h2>Dados da Equipe: ${formData.teamName}</h2>
                    ${studentsHtml}
                </body>
                </html>
            `;
        }

        // Função para gerar descrição da equipe usando a API Gemini
        generateDescriptionBtn.addEventListener('click', async () => {
            const teamName = teamNameInput.value.trim();
            if (!teamName) {
                showMessage("Por favor, insira o nome da equipe antes de gerar uma descrição.");
                return;
            }

            // Obter o número de alunos
            const numberOfStudents = studentsContainer.querySelectorAll('.student-section').length;

            loadingSpinner.style.display = 'inline-block'; // Mostra o spinner
            generateDescriptionBtn.disabled = true; // Desabilita o botão

            try {
                let chatHistory = [];
                const prompt = `Gere uma breve e empolgante descrição para uma equipe de robótica chamada "${teamName}", composta por ${numberOfStudents} alunos. A descrição deve ter no máximo 50 palavras e ser inspiradora para uma competição.`;
                chatHistory.push({ role: "user", parts: [{ text: prompt }] });
                const payload = { contents: chatHistory };
                const apiKey = ""; // API Key will be provided by Canvas runtime
                const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key=${apiKey}`;

                const response = await fetch(apiUrl, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });

                const result = await response.json();
                if (result.candidates && result.candidates.length > 0 &&
                    result.candidates[0].content && result.candidates[0].content.parts &&
                    result.candidates[0].content.parts.length > 0) {
                    const description = result.candidates[0].content.parts[0].text;
                    teamDescriptionOutput.textContent = description;
                    teamDescriptionOutput.classList.remove('hidden'); // Mostra o campo de descrição
                } else {
                    showMessage("Não foi possível gerar a descrição. Tente novamente.");
                    console.error("Erro na resposta da API Gemini:", result);
                }
            } catch (error) {
                console.error("Erro ao chamar a API Gemini:", error);
                showMessage("Ocorreu um erro ao gerar a descrição. Verifique sua conexão ou tente novamente.");
            } finally {
                loadingSpinner.style.display = 'none'; // Esconde o spinner
                generateDescriptionBtn.disabled = false; // Reabilita o botão
            }
        });

        // Event listener para adicionar aluno
        addStudentBtn.addEventListener('click', addStudentSection);

        // Event listener para o envio do formulário
        roboticsForm.addEventListener('submit', function(event) {
            event.preventDefault(); // Previne o envio padrão do formulário

            const formData = {
                teamName: document.getElementById('teamName').value,
                students: []
            };

            const studentSections = studentsContainer.querySelectorAll('.student-section');
            studentSections.forEach((section, index) => {
                const studentId = index + 1;
                const studentData = {
                    fullName: document.getElementById(`fullName_${studentId}`).value,
                    gradeClass: document.getElementById(`gradeClass_${studentId}`).value,
                    birthYear: document.getElementById(`birthYear_${studentId}`).value,
                    contactNumber: document.getElementById(`contactNumber_${studentId}`).value
                };
                formData.students.push(studentData);
            });

            // Abre uma nova janela com o conteúdo para impressão
            const printWindow = window.open('', '_blank');
            printWindow.document.write(generatePrintableContent(formData));
            printWindow.document.close();
            printWindow.focus();
            printWindow.print(); // Abre a caixa de diálogo de impressão
        });
    </script>
</body>
</html>
