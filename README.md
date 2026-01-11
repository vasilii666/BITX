<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BITX Games | Crash</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Roboto', sans-serif;
        }

        :root {
            --tg-blue: #3390ec;
            --tg-dark-blue: #2b7fd3;
            --tg-bg: #0f0f23;
            --tg-card: #1a1a2e;
            --tg-light: #2d2d44;
            --tg-text: #ffffff;
            --tg-text-secondary: #a0a0c0;
            --success: #4ade80;
            --danger: #f87171;
            --warning: #fbbf24;
            --glass-bg: rgba(26, 26, 46, 0.7);
            --glass-border: rgba(255, 255, 255, 0.1);
            --glass-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
        }

        body {
            background: var(--tg-bg);
            color: var(--tg-text);
            min-height: 100vh;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(51, 144, 236, 0.1) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(251, 191, 36, 0.1) 0%, transparent 20%);
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Стиль жидкого стекла */
        .glass {
            background: var(--glass-bg);
            backdrop-filter: blur(10px);
            -webkit-backdrop-filter: blur(10px);
            border-radius: 16px;
            border: 1px solid var(--glass-border);
            box-shadow: var(--glass-shadow);
            overflow: hidden;
        }

        /* Шапка */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            margin-bottom: 30px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .logo-icon {
            width: 50px;
            height: 50px;
            background: linear-gradient(135deg, var(--tg-blue), var(--warning));
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 24px;
            font-weight: bold;
        }

        .logo-text h1 {
            font-size: 28px;
            background: linear-gradient(to right, var(--tg-blue), var(--warning));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            letter-spacing: 1px;
        }

        .logo-text p {
            color: var(--tg-text-secondary);
            font-size: 14px;
        }

        .balance-container {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .balance-card {
            padding: 15px 25px;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
        }

        .balance-label {
            color: var(--tg-text-secondary);
            font-size: 14px;
            margin-bottom: 5px;
        }

        .balance-amount {
            font-size: 28px;
            font-weight: bold;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .balance-amount span {
            color: var(--warning);
        }

        .currency {
            color: var(--success);
            font-size: 18px;
        }

        /* Основной контент */
        .main-content {
            display: grid;
            grid-template-columns: 1fr 400px;
            gap: 30px;
        }

        /* Игровое поле */
        .game-area {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .game-container {
            padding: 30px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .timer-display {
            font-size: 120px;
            font-weight: bold;
            margin: 20px 0;
            text-align: center;
            background: linear-gradient(to right, var(--tg-blue), var(--warning));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 20px rgba(51, 144, 236, 0.3);
        }

        .crash-multiplier {
            font-size: 48px;
            margin: 10px 0 30px;
            font-weight: bold;
            color: var(--success);
            text-shadow: 0 0 10px rgba(74, 222, 128, 0.5);
        }

        .bet-controls {
            display: flex;
            flex-direction: column;
            width: 100%;
            gap: 20px;
            margin-top: 20px;
        }

        .bet-amount {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .bet-input-container {
            display: flex;
            align-items: center;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 12px;
            overflow: hidden;
            border: 1px solid var(--tg-light);
        }

        .bet-input-container input {
            flex: 1;
            padding: 15px;
            background: transparent;
            border: none;
            color: var(--tg-text);
            font-size: 18px;
            outline: none;
        }

        .bet-input-container .currency {
            padding: 0 15px;
            font-weight: bold;
            color: var(--warning);
        }

        .quick-bets {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .quick-bet {
            padding: 10px 15px;
            background: var(--tg-light);
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: 500;
        }

        .quick-bet:hover {
            background: var(--tg-blue);
            transform: translateY(-2px);
        }

        .direction-buttons {
            display: flex;
            gap: 15px;
            margin: 10px 0;
        }

        .direction-btn {
            flex: 1;
            padding: 18px;
            border-radius: 12px;
            border: none;
            font-size: 18px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .direction-up {
            background: linear-gradient(to right, var(--success), #22c55e);
            color: white;
        }

        .direction-down {
            background: linear-gradient(to right, var(--danger), #ef4444);
            color: white;
        }

        .direction-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }

        .direction-btn.active {
            transform: scale(0.98);
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.3);
        }

        .play-button {
            margin-top: 20px;
            padding: 22px;
            width: 100%;
            border-radius: 12px;
            border: none;
            background: linear-gradient(to right, var(--tg-blue), var(--tg-dark-blue));
            color: white;
            font-size: 22px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
        }

        .play-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 25px rgba(51, 144, 236, 0.3);
        }

        .play-button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            transform: none;
            box-shadow: none;
        }

        .play-button.running {
            background: linear-gradient(to right, var(--warning), #f59e0b);
        }

        /* Боковая панель с игроками */
        .players-sidebar {
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .players-container {
            padding: 25px;
            height: 500px;
            overflow-y: auto;
        }

        .section-title {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 20px;
            font-size: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid var(--tg-light);
        }

        .section-title i {
            color: var(--tg-blue);
        }

        .players-list {
            display: flex;
            flex-direction: column;
            gap: 15px;
        }

        .player-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border-radius: 12px;
            background: rgba(0, 0, 0, 0.2);
            transition: all 0.2s;
        }

        .player-item:hover {
            background: rgba(51, 144, 236, 0.1);
            transform: translateX(5px);
        }

        .player-info {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .player-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--tg-blue), var(--warning));
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
        }

        .player-name {
            font-weight: 500;
        }

        .player-bet {
            display: flex;
            flex-direction: column;
            align-items: flex-end;
        }

        .bet-amount {
            font-weight: bold;
            font-size: 18px;
            color: var(--warning);
        }

        .bet-direction {
            font-size: 12px;
            padding: 3px 8px;
            border-radius: 4px;
            margin-top: 5px;
        }

        .direction-up-badge {
            background: rgba(74, 222, 128, 0.2);
            color: var(--success);
        }

        .direction-down-badge {
            background: rgba(248, 113, 113, 0.2);
            color: var(--danger);
        }

        /* История игр */
        .history-container {
            padding: 25px;
        }

        .history-list {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .history-item {
            display: flex;
            justify-content: space-between;
            padding: 12px 15px;
            border-radius: 8px;
            background: rgba(0, 0, 0, 0.2);
        }

        .history-result {
            padding: 4px 10px;
            border-radius: 6px;
            font-weight: bold;
            font-size: 14px;
        }

        .history-win {
            background: rgba(74, 222, 128, 0.2);
            color: var(--success);
        }

        .history-loss {
            background: rgba(248, 113, 113, 0.2);
            color: var(--danger);
        }

        /* Адаптивность */
        @media (max-width: 1024px) {
            .main-content {
                grid-template-columns: 1fr;
            }
        }

        @media (max-width: 768px) {
            header {
                flex-direction: column;
                gap: 20px;
                align-items: flex-start;
            }
            
            .balance-container {
                align-self: stretch;
            }
            
            .balance-card {
                align-items: flex-start;
            }
            
            .timer-display {
                font-size: 80px;
            }
            
            .direction-buttons {
                flex-direction: column;
            }
        }

        /* Анимации */
        @keyframes pulse {
            0% { opacity: 0.8; }
            50% { opacity: 1; }
            100% { opacity: 0.8; }
        }

        .pulse {
            animation: pulse 1.5s infinite;
        }

        @keyframes countdown {
            from { transform: scale(1); }
            to { transform: scale(1.05); }
        }

        .countdown {
            animation: countdown 0.5s infinite alternate;
        }

        /* Полоса прокрутки */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.2);
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb {
            background: var(--tg-blue);
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: var(--tg-dark-blue);
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Шапка -->
        <header>
            <div class="logo">
                <div class="logo-icon glass">B</div>
                <div class="logo-text">
                    <h1>BITX Games</h1>
                    <p>Crash игра • 20 000 000 WC</p>
                </div>
            </div>
            <div class="balance-container">
                <div class="balance-card glass">
                    <div class="balance-label">Ваш баланс</div>
                    <div class="balance-amount">
                        <span id="balance">20 000 000</span>
                        <div class="currency">WC</div>
                    </div>
                </div>
            </div>
        </header>

        <!-- Основной контент -->
        <div class="main-content">
            <!-- Игровое поле -->
            <div class="game-area">
                <div class="game-container glass">
                    <div class="timer-display" id="timer">30.0</div>
                    <div class="crash-multiplier" id="multiplier">1.00x</div>
                    
                    <div class="bet-controls">
                        <div class="bet-amount">
                            <label for="betAmount">Сумма ставки</label>
                            <div class="bet-input-container glass">
                                <input type="number" id="betAmount" min="100" max="20000000" step="100" value="1000">
                                <div class="currency">WC</div>
                            </div>
                            <div class="quick-bets">
                                <div class="quick-bet" data-amount="100">100 WC</div>
                                <div class="quick-bet" data-amount="500">500 WC</div>
                                <div class="quick-bet" data-amount="1000">1 000 WC</div>
                                <div class="quick-bet" data-amount="5000">5 000 WC</div>
                                <div class="quick-bet" data-amount="10000">10 000 WC</div>
                            </div>
                        </div>
                        
                        <div class="direction-selection">
                            <label>Направление</label>
                            <div class="direction-buttons">
                                <button class="direction-btn direction-up" id="directionUp">
                                    <i class="fas fa-arrow-up"></i> Вверх
                                </button>
                                <button class="direction-btn direction-down" id="directionDown">
                                    <i class="fas fa-arrow-down"></i> Вниз
                                </button>
                            </div>
                        </div>
                        
                        <button class="play-button" id="playButton">
                            <i class="fas fa-play"></i> Сделать ставку
                        </button>
                    </div>
                </div>
            </div>
            
            <!-- Боковая панель с игроками -->
            <div class="players-sidebar">
                <div class="players-container glass">
                    <div class="section-title">
                        <i class="fas fa-users"></i>
                        <span>Игроки в текущем раунде</span>
                    </div>
                    <div class="players-list" id="playersList">
                        <!-- Список игроков будет добавляться динамически -->
                    </div>
                </div>
                
                <div class="history-container glass">
                    <div class="section-title">
                        <i class="fas fa-history"></i>
                        <span>История игр</span>
                    </div>
                    <div class="history-list" id="historyList">
                        <!-- История игр будет добавляться динамически -->
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Игровые переменные
        let balance = 20000000;
        let isGameRunning = false;
        let timer = 30;
        let timerInterval;
        let currentDirection = "up"; // "up" или "down"
        let currentMultiplier = 1.0;
        let players = [];
        let gameHistory = [];

        // DOM элементы
        const balanceElement = document.getElementById('balance');
        const timerElement = document.getElementById('timer');
        const multiplierElement = document.getElementById('multiplier');
        const betAmountInput = document.getElementById('betAmount');
        const directionUpButton = document.getElementById('directionUp');
        const directionDownButton = document.getElementById('directionDown');
        const playButton = document.getElementById('playButton');
        const playersList = document.getElementById('playersList');
        const historyList = document.getElementById('historyList');
        const quickBets = document.querySelectorAll('.quick-bet');

        // Имена игроков для генерации
        const playerNames = [
            "Alex", "BitcoinKing", "CryptoWolf", "LuckyStrike", "ProGamer", 
            "CryptoQueen", "MaxWin", "EasyMoney", "John", "Anna", "Mike", "Satoshi",
            "Vlad", "Kate", "Robert", "Lisa", "David", "Maria", "Paul", "Elena"
        ];

        // Инициализация
        function init() {
            updateBalanceDisplay();
            generateInitialPlayers();
            generateGameHistory();
            
            // Назначение обработчиков событий
            directionUpButton.addEventListener('click', () => setDirection('up'));
            directionDownButton.addEventListener('click', () => setDirection('down'));
            playButton.addEventListener('click', toggleGame);
            
            // Быстрые ставки
            quickBets.forEach(bet => {
                bet.addEventListener('click', () => {
                    betAmountInput.value = bet.getAttribute('data-amount');
                });
            });
            
            // Валидация ввода ставки
            betAmountInput.addEventListener('change', validateBetAmount);
            
            // Установка направления по умолчанию
            setDirection('up');
        }

        // Обновление отображения баланса
        function updateBalanceDisplay() {
            balanceElement.textContent = balance.toLocaleString('ru-RU');
        }

        // Установка направления ставки
        function setDirection(direction) {
            currentDirection = direction;
            
            if (direction === 'up') {
                directionUpButton.classList.add('active');
                directionDownButton.classList.remove('active');
            } else {
                directionUpButton.classList.add('active');
                directionUpButton.classList.remove('active');
                directionDownButton.classList.add('active');
            }
        }

        // Валидация суммы ставки
        function validateBetAmount() {
            let bet = parseInt(betAmountInput.value);
            
            if (isNaN(bet) || bet < 100) {
                betAmountInput.value = 100;
            } else if (bet > balance) {
                betAmountInput.value = balance;
            } else if (bet > 20000000) {
                betAmountInput.value = 20000000;
            }
        }

        // Генерация начальных игроков
        function generateInitialPlayers() {
            players = [];
            for (let i = 0; i < 8; i++) {
                const name = playerNames[Math.floor(Math.random() * playerNames.length)];
                const bet = Math.floor(Math.random() * 10000) + 100;
                const direction = Math.random() > 0.5 ? 'up' : 'down';
                
                players.push({
                    id: i,
                    name: name,
                    bet: bet,
                    direction: direction
                });
            }
            updatePlayersList();
        }

        // Обновление списка игроков
        function updatePlayersList() {
            playersList.innerHTML = '';
            
            players.forEach(player => {
                const playerElement = document.createElement('div');
                playerElement.className = 'player-item';
                
                playerElement.innerHTML = `
                    <div class="player-info">
                        <div class="player-avatar">${player.name.charAt(0)}</div>
                        <div class="player-name">${player.name}</div>
                    </div>
                    <div class="player-bet">
                        <div class="bet-amount">${player.bet.toLocaleString('ru-RU')} WC</div>
                        <div class="bet-direction ${player.direction === 'up' ? 'direction-up-badge' : 'direction-down-badge'}">
                            ${player.direction === 'up' ? 'Вверх' : 'Вниз'}
                        </div>
                    </div>
                `;
                
                playersList.appendChild(playerElement);
            });
        }

        // Генерация истории игр
        function generateGameHistory() {
            gameHistory = [];
            
            for (let i = 0; i < 10; i++) {
                const multiplier = (Math.random() * 2 + 0.5).toFixed(2);
                const win = Math.random() > 0.4;
                
                gameHistory.unshift({
                    multiplier: multiplier,
                    win: win
                });
            }
            
            updateHistoryList();
        }

        // Обновление истории игр
        function updateHistoryList() {
            historyList.innerHTML = '';
            
            gameHistory.forEach(game => {
                const historyItem = document.createElement('div');
                historyItem.className = 'history-item';
                
                historyItem.innerHTML = `
                    <div>${game.multiplier}x</div>
                    <div class="history-result ${game.win ? 'history-win' : 'history-loss'}">
                        ${game.win ? 'Выигрыш' : 'Проигрыш'}
                    </div>
                `;
                
                historyList.appendChild(historyItem);
            });
        }

        // Добавление нового игрока
        function addPlayer() {
            const name = playerNames[Math.floor(Math.random() * playerNames.length)];
            const bet = parseInt(betAmountInput.value);
            const direction = currentDirection;
            
            players.unshift({
                id: players.length,
                name: name,
                bet: bet,
                direction: direction
            });
            
            // Ограничиваем список 10 игроками
            if (players.length > 10) {
                players.pop();
            }
            
            updatePlayersList();
        }

        // Запуск/остановка игры
        function toggleGame() {
            if (isGameRunning) {
                stopGame();
            } else {
                startGame();
            }
        }

        // Запуск игры
        function startGame() {
            const bet = parseInt(betAmountInput.value);
            
            if (bet > balance) {
                alert('Недостаточно средств на балансе!');
                return;
            }
            
            if (bet < 100) {
                alert('Минимальная ставка - 100 WC!');
                return;
            }
            
            // Вычитаем ставку из баланса
            balance -= bet;
            updateBalanceDisplay();
            
            // Добавляем игрока в список
            addPlayer();
            
            // Меняем состояние игры
            isGameRunning = true;
            playButton.disabled = true;
            playButton.classList.add('running');
            playButton.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Идет игра...';
            
            // Сбрасываем таймер и множитель
            timer = 30;
            currentMultiplier = 1.0;
            timerElement.textContent = timer.toFixed(1);
            multiplierElement.textContent = currentMultiplier.toFixed(2) + 'x';
            
            // Запускаем таймер
            timerInterval = setInterval(updateGame, 100);
        }

        // Обновление игрового процесса
        function updateGame() {
            timer -= 0.1;
            
            if (timer <= 0) {
                finishGame();
                return;
            }
            
            // Обновляем таймер
            timerElement.textContent = timer.toFixed(1);
            
            // Увеличиваем множитель с разной скоростью в зависимости от направления
            const increment = currentDirection === 'up' ? 0.03 : 0.02;
            currentMultiplier += increment;
            
            // Добавляем случайность
            currentMultiplier += (Math.random() - 0.5) * 0.01;
            
            // Обновляем отображение множителя
            multiplierElement.textContent = currentMultiplier.toFixed(2) + 'x';
            
            // Анимация для последних 5 секунд
            if (timer < 5) {
                timerElement.classList.add('countdown');
                multiplierElement.classList.add('pulse');
            }
        }

        // Завершение игры
        function finishGame() {
            clearInterval(timerInterval);
            
            // Определяем результат
            const targetMultiplier = (Math.random() * 2 + 0.5).toFixed(2);
            const win = (currentDirection === 'up' && currentMultiplier >= targetMultiplier) || 
                        (currentDirection === 'down' && currentMultiplier <= targetMultiplier);
            
            // Вычисляем выигрыш
            const bet = parseInt(betAmountInput.value);
            let winAmount = 0;
            
            if (win) {
                // Коэффициент выигрыша с учетом комиссии 0.2%
                const winMultiplier = currentDirection === 'up' ? currentMultiplier : 2.0 - currentMultiplier;
                winAmount = Math.floor(bet * winMultiplier * 0.998); // Учитываем комиссию 0.2%
                balance += winAmount;
            }
            
            // Добавляем игру в историю
            gameHistory.unshift({
                multiplier: currentMultiplier.toFixed(2),
                win: win
            });
            
            if (gameHistory.length > 10) {
                gameHistory.pop();
            }
            
            // Обновляем интерфейс
            updateBalanceDisplay();
            updateHistoryList();
            
            // Показываем результат
            alert(win ? 
                `Поздравляем! Вы выиграли ${winAmount.toLocaleString('ru-RU')} WC! Множитель: ${currentMultiplier.toFixed(2)}x` : 
                `Игра завершена. Вы проиграли ${bet.toLocaleString('ru-RU')} WC. Множитель: ${currentMultiplier.toFixed(2)}x`);
            
            // Сбрасываем состояние игры
            isGameRunning = false;
            playButton.disabled = false;
            playButton.classList.remove('running');
            playButton.innerHTML = '<i class="fas fa-play"></i> Сделать ставку';
            
            timerElement.classList.remove('countdown');
            multiplierElement.classList.remove('pulse');
            
            // Сброс таймера
            timer = 30;
            timerElement.textContent = timer.toFixed(1);
            multiplierElement.textContent = '1.00x';
            
            // Обновляем список игроков
            generateInitialPlayers();
        }

        // Остановка игры (досрочная)
        function stopGame() {
            clearInterval(timerInterval);
            
            isGameRunning = false;
            playButton.disabled = false;
            playButton.classList.remove('running');
            playButton.innerHTML = '<i class="fas fa-play"></i> Сделать ставку';
            
            timerElement.classList.remove('countdown');
            multiplierElement.classList.remove('pulse');
            
            // Сброс таймера
            timer = 30;
            timerElement.textContent = timer.toFixed(1);
            multiplierElement.textContent = '1.00x';
            
            alert('Игра остановлена досрочно. Ставка возвращена на баланс.');
        }

        // Запуск при загрузке страницы
        window.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
