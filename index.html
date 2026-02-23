import React, { useState, useEffect, useRef, useCallback } from 'react';
import { Volume2, VolumeX, Droplet, Hand, Info, Sun, Snowflake, CloudRain, Leaf, Moon, FastForward } from 'lucide-react';

// --- BAZA WIEDZY (ELEMENTY EDUKACYJNE) ---
const PLANTS = {
  carrot: {
    id: 'carrot',
    name: 'Marchew',
    emoji: '🥕',
    sproutEmoji: '🌱',
    price: 10,
    growTime: 7, // dni
    plantSeasons: ['Wiosna', 'Lato'],
    harvestSeasons: ['Lato', 'Jesień'],
    waterNeeds: 1, 
    eduText: 'Marchew (Daucus carota) to warzywo korzeniowe bogate w beta-karoten, który w organizmie ludzkim przekształca się w witaminę A. Najlepiej rośnie w spulchnionej glebie. Należy ją siać rzadko, aby korzenie miały miejsce na rozwój.'
  },
  tomato: {
    id: 'tomato',
    name: 'Pomidor',
    emoji: '🍅',
    sproutEmoji: '🌿',
    price: 15,
    growTime: 12,
    plantSeasons: ['Wiosna'],
    harvestSeasons: ['Lato', 'Jesień'],
    waterNeeds: 2,
    eduText: 'Pomidor (Solanum lycopersicum) pochodzi z Ameryki Południowej. Jest to roślina ciepłolubna, dlatego w Polsce sadzi się ją z rozsady dopiero po "Zimnej Zośce" (połowa maja). Wymaga dużo słońca i regularnego, ale nie nadmiernego podlewania.'
  },
  sunflower: {
    id: 'sunflower',
    name: 'Słonecznik',
    emoji: '🌻',
    sproutEmoji: '🌱',
    price: 20,
    growTime: 15,
    plantSeasons: ['Wiosna'],
    harvestSeasons: ['Lato', 'Jesień'],
    waterNeeds: 1,
    eduText: 'Słonecznik zwyczajny (Helianthus annuus) znany jest ze zjawiska heliotropizmu – jego młode kwiatostany podążają za słońcem w ciągu dnia. Jego nasiona są doskonałym źródłem witaminy E i zdrowych tłuszczów.'
  },
  pumpkin: {
    id: 'pumpkin',
    name: 'Dynia',
    emoji: '🎃',
    sproutEmoji: '🌿',
    price: 25,
    growTime: 20,
    plantSeasons: ['Wiosna'],
    harvestSeasons: ['Jesień'],
    waterNeeds: 3,
    eduText: 'Dynia to roślina o bardzo dużych wymaganiach pokarmowych i wodnych. Posiada płytki system korzeniowy. Jej owoce mogą być przechowywane przez całą zimę, dostarczając cennych witamin w okresie chłodów.'
  },
  garlic: {
    id: 'garlic',
    name: 'Czosnek',
    emoji: '🧄',
    sproutEmoji: '🧄',
    price: 30,
    growTime: 25,
    plantSeasons: ['Jesień'],
    harvestSeasons: ['Lato'], 
    waterNeeds: 0.5,
    eduText: 'Czosnek (Allium sativum) to naturalny antybiotyk dzięki zawartości allicyny. W Polsce bardzo popularny jest czosnek ozimy, który sadzi się jesienią, by zdążył się ukorzenić przed zimą, a plonuje w połowie lata.'
  }
};

const SEASONS = ['Wiosna', 'Lato', 'Jesień', 'Zima'];
const DAYS_PER_SEASON = 30;
const BASE_TICK_RATE = 2000; // Podstawowy czas trwania dnia w ms

// --- SYSTEM AUDIO (Web Audio API) ---
class SoundEngine {
  constructor() {
    this.ctx = null;
    this.bgmOscillator = null;
    this.bgmGain = null;
    this.isPlaying = false;
    this.bgmInterval = null;
    this.currentSpeed = 1;
  }

  init() {
    if (!this.ctx) {
      this.ctx = new (window.AudioContext || window.webkitAudioContext)();
    }
    if (this.ctx.state === 'suspended') {
      this.ctx.resume();
    }
  }

  playTone(freq, type, duration, vol = 0.1) {
    if (!this.ctx) return;
    const osc = this.ctx.createOscillator();
    const gain = this.ctx.createGain();
    osc.type = type;
    osc.frequency.setValueAtTime(freq, this.ctx.currentTime);
    gain.gain.setValueAtTime(vol, this.ctx.currentTime);
    gain.gain.exponentialRampToValueAtTime(0.01, this.ctx.currentTime + duration);
    osc.connect(gain);
    gain.connect(this.ctx.destination);
    osc.start();
    osc.stop(this.ctx.currentTime + duration);
  }

  playPlant() {
    this.init();
    this.playTone(300, 'sine', 0.1, 0.2);
    setTimeout(() => this.playTone(400, 'sine', 0.1, 0.2), 50);
  }

  playWater() {
    this.init();
    for(let i=0; i<5; i++) {
        setTimeout(() => this.playTone(100 + Math.random()*200, 'square', 0.1, 0.05), i*30);
    }
  }

  playHarvest() {
    this.init();
    this.playTone(523.25, 'sine', 0.1, 0.1);
    setTimeout(() => this.playTone(659.25, 'sine', 0.1, 0.1), 100);
    setTimeout(() => this.playTone(783.99, 'sine', 0.2, 0.1), 200);
    setTimeout(() => this.playTone(1046.50, 'sine', 0.3, 0.15), 300);
  }

  playError() {
    this.init();
    this.playTone(150, 'sawtooth', 0.2, 0.1);
  }

  updateSpeed(speed) {
    this.currentSpeed = speed;
    if (this.isPlaying) {
      this.toggleBGM(false);
      this.toggleBGM(true);
    }
  }

  toggleBGM(enable) {
    this.init();
    if (enable && !this.isPlaying) {
      this.isPlaying = true;
      const notes = [261.63, 329.63, 392.00, 523.25, 392.00, 329.63];
      let step = 0;
      // Dostosowujemy tempo muzyki do prędkości gry, ale z ograniczeniem dla czytelności
      const intervalTime = 600 / Math.sqrt(this.currentSpeed);
      this.bgmInterval = setInterval(() => {
        if(this.ctx.state === 'running') {
            this.playTone(notes[step % notes.length], 'sine', 0.5, 0.03);
            step++;
        }
      }, intervalTime);
    } else if (!enable && this.isPlaying) {
      this.isPlaying = false;
      clearInterval(this.bgmInterval);
    }
  }
}

const sfx = new SoundEngine();

export default function App() {
  const [seasonIndex, setSeasonIndex] = useState(0);
  const [day, setDay] = useState(1);
  const [money, setMoney] = useState(50);
  const [audioEnabled, setAudioEnabled] = useState(false);
  const [darkMode, setDarkMode] = useState(false);
  const [gameSpeed, setGameSpeed] = useState(1); // 1, 2, 5
  const [activeTool, setActiveTool] = useState('water');
  const [infoText, setInfoText] = useState('Witaj w Ogródku Działkowym! Wybierz narzędzie lub nasiona z paska, aby rozpocząć pracę. Pamiętaj, każda roślina ma swoje wymagania.');
  const [eduTitle, setEduTitle] = useState('Poradnik Działkowca');

  const [plots, setPlots] = useState(Array(9).fill({
    plantId: null,
    growth: 0,
    watered: false,
    dead: false
  }));

  const plotsRef = useRef(plots);
  const seasonIndexRef = useRef(seasonIndex);
  plotsRef.current = plots;
  seasonIndexRef.current = seasonIndex;

  // Główna pętla gry
  useEffect(() => {
    const timer = setInterval(() => {
      setDay(prevDay => {
        let nextDay = prevDay + 1;
        let nextSeasonIdx = seasonIndexRef.current;
        
        if (nextDay > DAYS_PER_SEASON) {
          nextDay = 1;
          nextSeasonIdx = (nextSeasonIdx + 1) % 4;
          setSeasonIndex(nextSeasonIdx);
        }

        const currentSeason = SEASONS[nextSeasonIdx];
        const newPlots = plotsRef.current.map(plot => {
          if (!plot.plantId || plot.dead) return plot;
          
          let newGrowth = plot.growth;
          let newWatered = plot.watered;
          let newDead = plot.dead;

          if (plot.watered) {
             newGrowth += 1;
             newWatered = false; 
          }

          if (currentSeason === 'Zima' && plot.plantId !== 'garlic') {
              newDead = true;
          }

          return { ...plot, growth: newGrowth, watered: newWatered, dead: newDead };
        });

        setPlots(newPlots);
        return nextDay;
      });
    }, BASE_TICK_RATE / gameSpeed);

    return () => clearInterval(timer);
  }, [gameSpeed]);

  // Obsługa Audio
  useEffect(() => {
    sfx.updateSpeed(gameSpeed);
    sfx.toggleBGM(audioEnabled);
  }, [audioEnabled, gameSpeed]);

  const handlePlotClick = (index) => {
    const plot = plots[index];
    const currentSeason = SEASONS[seasonIndex];
    let newPlots = [...plots];

    if (activeTool === 'water') {
      if (plot.plantId && !plot.dead && !plot.watered) {
        newPlots[index] = { ...plot, watered: true };
        setPlots(newPlots);
        if(audioEnabled) sfx.playWater();
      } else {
         if(audioEnabled) sfx.playError();
      }
    } 
    else if (activeTool === 'harvest') {
      if (plot.plantId) {
        const plantDef = PLANTS[plot.plantId];
        if (plot.growth >= plantDef.growTime && !plot.dead) {
          if (plantDef.harvestSeasons.includes(currentSeason)) {
            setMoney(m => m + plantDef.price * 2);
            setInfoText(`Zebrałeś ${plantDef.name}! Sprzedano za ${plantDef.price * 2} monet.`);
            if(audioEnabled) sfx.playHarvest();
          } else {
            setInfoText(`${plantDef.name} nie owocuje w porze: ${currentSeason}. Zbiór zepsuty.`);
            if(audioEnabled) sfx.playError();
          }
        } else if (plot.dead) {
          setInfoText('Usunięto zwiędłą roślinę. Przygotuj glebę pod nowe sadzonki.');
          if(audioEnabled) sfx.playWater();
        } else {
          setInfoText('Roślina jeszcze nie urosła! Daj jej czas i wodę.');
          if(audioEnabled) sfx.playError();
          return;
        }
        newPlots[index] = { plantId: null, growth: 0, watered: false, dead: false };
        setPlots(newPlots);
      }
    } 
    else if (PLANTS[activeTool]) {
      const plantDef = PLANTS[activeTool];
      if (plot.plantId) {
        setInfoText('To pole jest już zajęte!');
        if(audioEnabled) sfx.playError();
        return;
      }
      
      if (money < plantDef.price) {
        setInfoText('Za mało monet na te nasiona!');
        if(audioEnabled) sfx.playError();
        return;
      }

      if (!plantDef.plantSeasons.includes(currentSeason)) {
         setInfoText(`${plantDef.name} sadzi się w porach: ${plantDef.plantSeasons.join(', ')}. Teraz jest ${currentSeason}. Roślina może się nie przyjąć!`);
         if(audioEnabled) sfx.playError();
      }

      setMoney(m => m - plantDef.price);
      newPlots[index] = { plantId: activeTool, growth: 0, watered: false, dead: false };
      setPlots(newPlots);
      if(audioEnabled) sfx.playPlant();
      
      setEduTitle(`Edukacja: ${plantDef.name}`);
      setInfoText(plantDef.eduText);
    }
  };

  const cycleSpeed = () => {
    const speeds = [1, 2, 5];
    const currentIndex = speeds.indexOf(gameSpeed);
    const nextSpeed = speeds[(currentIndex + 1) % speeds.length];
    setGameSpeed(nextSpeed);
    setInfoText(`Prędkość gry ustawiona na: ${nextSpeed}x`);
  };

  const getSeasonColor = () => {
    switch(seasonIndex) {
      case 0: return 'bg-emerald-600';
      case 1: return 'bg-yellow-500'; 
      case 2: return 'bg-orange-600'; 
      case 3: return 'bg-blue-300';   
      default: return 'bg-gray-500';
    }
  };

  const getSeasonIcon = () => {
    switch(seasonIndex) {
      case 0: return <Leaf className="w-6 h-6 text-white" />;
      case 1: return <Sun className="w-6 h-6 text-white" />;
      case 2: return <CloudRain className="w-6 h-6 text-white" />;
      case 3: return <Snowflake className="w-6 h-6 text-white" />;
      default: return null;
    }
  };

  return (
    <div className={darkMode ? 'dark' : ''}>
      <div className="min-h-screen bg-stone-100 dark:bg-stone-900 font-sans flex flex-col items-center py-4 px-2 sm:px-4 transition-colors duration-300">
        
        {/* NAGŁÓWEK GRY */}
        <div className="w-full max-w-2xl bg-white dark:bg-stone-800 rounded-2xl shadow-lg overflow-hidden mb-4 transition-colors duration-300">
          <div className={`${getSeasonColor()} p-4 flex justify-between items-center transition-colors duration-1000`}>
            <div className="flex items-center space-x-2">
              {getSeasonIcon()}
              <h1 className="text-white font-bold text-xl tracking-wide">Ogródek Działkowy</h1>
            </div>
            <div className="flex items-center space-x-2">
              <button 
                onClick={cycleSpeed}
                className="p-2 bg-white/20 hover:bg-white/30 rounded-full text-white transition flex items-center space-x-1"
                title="Przyspiesz czas"
              >
                <FastForward size={18} />
                <span className="text-xs font-bold">{gameSpeed}x</span>
              </button>
              <button 
                onClick={() => setDarkMode(!darkMode)}
                className="p-2 bg-white/20 hover:bg-white/30 rounded-full text-white transition"
                aria-label="Przełącz motyw"
              >
                {darkMode ? <Sun size={20} /> : <Moon size={20} />}
              </button>
              <button 
                onClick={() => setAudioEnabled(!audioEnabled)}
                className="p-2 bg-white/20 hover:bg-white/30 rounded-full text-white transition"
                aria-label="Przełącz dźwięk"
              >
                {audioEnabled ? <Volume2 size={20} /> : <VolumeX size={20} />}
              </button>
            </div>
          </div>

          <div className="p-4 flex justify-between items-center bg-stone-50 dark:bg-stone-800/50 border-b border-stone-200 dark:border-stone-700 transition-colors duration-300">
            <div className="text-lg font-semibold text-stone-700 dark:text-stone-300">
              Pora roku: <span className="text-emerald-700 dark:text-emerald-400">{SEASONS[seasonIndex]}</span> (Dzień {day}/30)
            </div>
            <div className="text-lg font-bold text-yellow-600 dark:text-yellow-400 bg-yellow-100 dark:bg-yellow-900/30 px-4 py-1 rounded-full shadow-sm transition-colors duration-300">
              🪙 {money}
            </div>
          </div>
        </div>

        {/* GŁÓWNY PANEL Z SIATKĄ I NARZĘDZIAMI */}
        <div className="w-full max-w-2xl grid md:grid-cols-3 gap-4">
          
          <div className="md:col-span-2 bg-[#8B5A2B] dark:bg-[#6e4620] p-4 rounded-2xl shadow-inner border-4 border-[#654321] dark:border-[#4a3118] aspect-square grid grid-cols-3 gap-2 transition-colors duration-300">
            {plots.map((plot, idx) => {
              const isGrown = plot.plantId && plot.growth >= PLANTS[plot.plantId].growTime;
              
              return (
                <div 
                  key={idx}
                  onClick={() => handlePlotClick(idx)}
                  className={`
                    relative rounded-lg cursor-pointer transition-all duration-300 shadow-md flex items-center justify-center text-4xl sm:text-5xl
                    ${plot.watered ? 'bg-[#5c3a21] dark:bg-[#472c18] border-2 border-[#3d2615] dark:border-[#2b1b0e]' : 'bg-[#a06836] dark:bg-[#85552a] hover:bg-[#b07846] dark:hover:bg-[#966232] border-2 border-[#825227] dark:border-[#6b421d]'}
                    ${plot.dead ? 'grayscale opacity-60' : ''}
                  `}
                >
                  {plot.plantId && !plot.dead && (
                    <div className="animate-bounce-short">
                      {plot.growth === 0 ? '🌰' : (isGrown ? PLANTS[plot.plantId].emoji : PLANTS[plot.plantId].sproutEmoji)}
                    </div>
                  )}
                  
                  {plot.dead && '🥀'}

                  {plot.plantId && !plot.watered && !plot.dead && !isGrown && (
                    <div className="absolute top-1 right-1 w-3 h-3 bg-blue-400 rounded-full animate-pulse border border-white dark:border-stone-800"></div>
                  )}
                  
                  {isGrown && !plot.dead && (
                    <div className="absolute inset-0 border-4 border-yellow-400 rounded-lg animate-pulse opacity-50 pointer-events-none"></div>
                  )}
                </div>
              );
            })}
          </div>

          <div className="flex flex-col gap-2">
            <div className="bg-white dark:bg-stone-800 p-3 rounded-xl shadow-md transition-colors duration-300">
              <h3 className="text-sm font-bold text-stone-500 dark:text-stone-400 uppercase tracking-wider mb-2">Akcje</h3>
              <div className="grid grid-cols-2 gap-2">
                <button 
                  onClick={() => { setActiveTool('water'); setEduTitle('Podlewanie'); setInfoText('Podlewaj rośliny każdego dnia. Bez wody zatrzymają swój wzrost.'); }}
                  className={`flex flex-col items-center justify-center p-3 rounded-lg border-2 transition ${activeTool === 'water' ? 'border-blue-500 bg-blue-50 text-blue-700 dark:bg-blue-900/30 dark:text-blue-400' : 'border-stone-200 dark:border-stone-700 hover:bg-stone-50 dark:hover:bg-stone-700 text-stone-600 dark:text-stone-300'}`}
                >
                  <Droplet className="mb-1" />
                  <span className="text-xs font-semibold">Podlej</span>
                </button>
                <button 
                  onClick={() => { setActiveTool('harvest'); setEduTitle('Zbiory i Porządki'); setInfoText('Zbieraj wyrośnięte plony w odpowiedniej porze roku, by zarobić. Usuwaj zwiędłe rośliny.'); }}
                  className={`flex flex-col items-center justify-center p-3 rounded-lg border-2 transition ${activeTool === 'harvest' ? 'border-amber-500 bg-amber-50 text-amber-700 dark:bg-amber-900/30 dark:text-amber-400' : 'border-stone-200 dark:border-stone-700 hover:bg-stone-50 dark:hover:bg-stone-700 text-stone-600 dark:text-stone-300'}`}
                >
                  <Hand className="mb-1" />
                  <span className="text-xs font-semibold">Zbiory</span>
                </button>
              </div>
            </div>

            <div className="bg-white dark:bg-stone-800 p-3 rounded-xl shadow-md flex-grow transition-colors duration-300">
              <h3 className="text-sm font-bold text-stone-500 dark:text-stone-400 uppercase tracking-wider mb-2">Nasiona (Sklep)</h3>
              <div className="flex flex-col gap-2 overflow-y-auto max-h-[300px] pr-1">
                {Object.values(PLANTS).map(plant => (
                  <button
                    key={plant.id}
                    onClick={() => {
                      setActiveTool(plant.id);
                      setEduTitle(`Nasiona: ${plant.name}`);
                      setInfoText(plant.eduText);
                    }}
                    className={`flex items-center p-2 rounded-lg border-2 transition ${activeTool === plant.id ? 'border-emerald-500 bg-emerald-50 dark:bg-emerald-900/30 dark:border-emerald-500' : 'border-stone-200 dark:border-stone-700 hover:bg-stone-50 dark:hover:bg-stone-700'} ${money < plant.price ? 'opacity-60 grayscale' : ''}`}
                  >
                    <span className="text-2xl mr-3">{plant.emoji}</span>
                    <div className="text-left flex-grow">
                      <div className="font-bold text-stone-800 dark:text-stone-200 text-sm">{plant.name}</div>
                      <div className="text-xs text-stone-500 dark:text-stone-400">Kosz: {plant.price} 🪙</div>
                    </div>
                    <div className="text-[10px] text-right text-stone-400 dark:text-stone-500 leading-tight">
                      {plant.plantSeasons.map(s => s.substring(0,3)).join('/')}
                    </div>
                  </button>
                ))}
              </div>
            </div>
          </div>

        </div>

        {/* PANEL EDUKACYJNY I INFORMACYJNY */}
        <div className="w-full max-w-2xl bg-blue-50 dark:bg-blue-900/20 border-l-4 border-blue-400 dark:border-blue-600 p-4 rounded-r-xl shadow-md mt-4 flex gap-4 transition-colors duration-300">
          <Info className="text-blue-500 dark:text-blue-400 flex-shrink-0 mt-1" />
          <div>
            <h4 className="font-bold text-blue-900 dark:text-blue-300 mb-1">{eduTitle}</h4>
            <p className="text-sm text-blue-800 dark:text-blue-400/90 leading-relaxed">
              {infoText}
            </p>
          </div>
        </div>

        {/* FOOTER - AUTOR */}
        <footer className="mt-8 mb-4 text-center text-stone-500 dark:text-stone-400 text-sm transition-colors duration-300">
          Stworzone z pasją do ogrodnictwa i programowania przez{' '}
          <a 
            href="https://linktr.ee/kitadamian" 
            target="_blank" 
            rel="noopener noreferrer"
            className="font-bold text-emerald-600 dark:text-emerald-500 hover:text-emerald-700 dark:hover:text-emerald-400 transition underline decoration-emerald-300 dark:decoration-emerald-700"
          >
            Damian Kita
          </a>
        </footer>

        <style dangerouslySetInnerHTML={{__html: `
          @keyframes bounce-short {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
          }
          .animate-bounce-short {
            animation: bounce-short 1.5s ease-in-out infinite;
          }
        `}} />
      </div>
    </div>
  );
}