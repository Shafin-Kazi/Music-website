const music = new Audio('audio/Born to Shine.mp3');
// music.play();
let isShuffle = false; // Track if shuffle is active
let index = 2;

const song = [
  {
    id: "1",
    songName: `Old Money<br>
                        <div class="subtitle">
                            Ap Dhillon
                        </div>`,
    poster: "img/Old_money.jpg",
    songAdd: "audio/Old Money.mp3"
  },
  {
    id: "2",
    songName: `Born to Shine<br>
                        <div class="subtitle">
                            Diljit Dosanjh
                        </div>`,
    poster: "img/2.jpeg",
    songAdd: "audio/Born to Shine.mp3"
  },
  {
    id: "3",
    songName: `Lemonade<br>
                        <div class="subtitle">
                            Diljit Dosanjh
                        </div>`,
    poster: "img/3.jpg",
    songAdd: "audio/Lemonade.mp3"
  },
  {
    id: "4",
    songName: `O Maahi<br>
                        <div class="subtitle">
                            Arijit Singh
                        </div>`,
    poster: "img/4.jpg",
    songAdd: "audio/O Maahi.mp3"
  },
  {
    id: "5",
    songName: `Aaj Ki Raat<br>
                        <div class="subtitle">
                            Madhubanti Bagchi, Divya Kumar, Sachin -Jigar
                        </div>`,
    poster: "img/5.jpg",
    songAdd: "audio/Aaj Ki Raat.mp3"
  },
  {
    id: "6",
    songName: `See you again<br>
                        <div class="subtitle">
                            Wiz Khalifa
                        </div>`,
    poster: "img/6.jpeg",
    songAdd: "audio/See you again.mp3"
  },
  {
    id: "7",
    songName: `Dekha Tenu<br>
                        <div class="subtitle">
                            Udit Narayan
                        </div>`,
    poster: "img/7.jpg",
    songAdd: "audio/Dekha Tenu.mp3"
  },
  {
    id: "8",
    songName: `On My Way<br>
                            <div class="subtitle">
                                Alan Walker
                            </div>`,
    poster: "img/Alan_Walker_-_On_My_Way.png",
    songAdd: "audio/On My Way.mp3"
  },
  {
    id: "9",
    songName: `Pasoori<br>
                            <div class="subtitle">
                                Shae Gill, Ali Sethi
                            </div>`,
    poster: "img/pasoori.jpeg",
    songAdd: "audio/Pasoori.mp3"
  },
  {
    id: "10",
    songName: `Kesariya<br>
                            <div class="subtitle">
                                Arijit Singh
                            </div>`,
    poster: "img/kesariya.jpg",
    songAdd: "audio/Kesariya.mp3"
  },
  {
    id: "11",
    songName: `Obsessed<br>
                            <div class="subtitle">
                                Riar Saab, Abhijay Sharma
                            </div>`,
    poster: "img/obsessed.jpeg",
    songAdd: "audio/Obsessed.mp3"
  },
  {
    id: "12",
    songName: `Lalkara<br>
                            <div class="subtitle">
                                Diljit Dosanjh, Intense, Sultaan
                            </div>`,
    poster: "img/Lalkara.jpg",
    songAdd: "audio/Lalkara.mp3"
  },
  {
    id: "13",
    songName: `California Love<br>
                            <div class="subtitle">
                                Cheema Y, Gur Sindhu
                            </div>`,
    poster: "img/californialove.jpeg",
    songAdd: "audio/California Love.mp3"
  }
]

Array.from(document.getElementsByClassName("songitems")).forEach((e, i) => {
  e.getElementsByTagName("img")[0].src = song[i].poster;
  e.getElementsByTagName("h5")[0].innerHTML = song[i].songName;
})

let masterPlay = document.getElementById("masterPlay");
let wave = document.getElementById("wave");

masterPlay.addEventListener("click", () => {
  if (music.paused || music.currentTime <= 0) {
    music.play();
    wave.classList.add("active1")
    masterPlay.classList.remove("bi-play-fill");
    masterPlay.classList.add("bi-pause-fill");
  } else {
    music.pause();
    wave.classList.remove("active1")
    masterPlay.classList.add("bi-play-fill");
    masterPlay.classList.remove("bi-pause-fill");
  }
})

Array.from(document.getElementsByClassName("playListPlay")).forEach((e) => {
  e.addEventListener("click", (el) => {
    index = el.target.id;
    // console.log(index)

    playSong(index)
  })
})

let currentstart = document.getElementById("currentstart")
let currentend = document.getElementById("currentend")
let seek = document.getElementById("seek")
let dot = document.getElementsByClassName("dot")[0]

music.addEventListener("timeupdate", () => {
  let m_currenttime = music.currentTime;
  let m_duration = music.duration;

  if (!isNaN(m_duration)) {
    let min1 = Math.floor(m_duration / 60);
    let sec1 = Math.floor(m_duration % 60);
    if (sec1 < 10) {
      sec1 = `0${sec1}`;
    }
    currentend.innerText = `${min1}:${sec1}`;
  }

  let min2 = Math.floor(m_currenttime / 60);
  let sec2 = Math.floor(m_currenttime % 60);
  if (sec2 < 10) {
    sec2 = `0${sec2}`;
  }
  currentstart.innerText = `${min2}:${sec2}`;

  let progressbar = parseInt((m_currenttime / m_duration) * 100)
  seek.value = progressbar
  // console.log(seek.value)
  bar2.style.width = `${seek.value}%`
  dot.style.left = `${seek.value}%`
})

seek.addEventListener("change", () => {
  music.currentTime = (seek.value * music.duration) / 100
})

let vol = document.getElementById("vol")
let vol_dot = document.getElementById("vol_dot")
let vol_bar = document.getElementsByClassName("vol_bar")[0]
vol.addEventListener("change", () => {
  console.log(vol.value)
  vol_bar.style.width = `${vol.value}%`
  vol_dot.style.left = `${vol.value}%`
  music.volume = vol.value / 100;
})

let previousSong = document.getElementById("previousSong")
previousSong.addEventListener("click", () => {
  index--
  if (index < 1) {
    index = song.length
  }
  playSong(index)
})
let nextSong = document.getElementById("nextSong")
nextSong.addEventListener("click", () => {
  index++
  if (index > song.length) {
    index = 1
  }
  playSong(index)
})

let download = document.getElementById("download");
download.addEventListener("click", () => {
  let songdownload = song[index - 1];
  download.href = songdownload.songAdd;
  download.setAttribute('download', `${songdownload.songName.split('<br>')[0].trim()}.mp3`);
});


let shuffle = document.getElementsByClassName("shuffle")[0];

shuffle.addEventListener("click", () => {
  isShuffle = !isShuffle; // Toggle shuffle state
  if (isShuffle) {
    shuffle.classList.remove("bi-music-note-beamed");
    shuffle.classList.add("bi-shuffle");
    getShuffle(); // Start with a shuffled song
  } else {
    shuffle.classList.add("bi-music-note-beamed");
    shuffle.classList.remove("bi-shuffle");
  }
});

music.addEventListener("ended", () => {
  if (isShuffle) {
    getShuffle(); // Play a new shuffled song
  } else {
    index++; // Move to the next song in order
    if (index > song.length) {
      index = 1; // Loop back to the first song
    }
    playSong(index);
  }
});














let pop_song_left = document.getElementById("pop_song_left");
let pop_song_right = document.getElementById('pop_song_right');
let pop_song = document.getElementsByClassName('pop_song')[0];

let item_left = document.getElementById("item_left");
let item_right = document.getElementById("item_right");
let item = document.getElementsByClassName("item")[0];

pop_song_right.addEventListener('click', () => {
  pop_song.scrollLeft += 118;
});
pop_song_left.addEventListener('click', () => {
  pop_song.scrollLeft -= 118;
});

item_right.addEventListener('click', () => {
  item.scrollLeft += 80;
});
item_left.addEventListener('click', () => {
  item.scrollLeft -= 80;
});

function playSong(index) {
  let selectedSong = song[index - 1];
  if (selectedSong) {
    music.src = selectedSong.songAdd;
    music.play();
    wave.classList.add("active1");
    document.getElementById("titleImage").src = selectedSong.poster;
    document.getElementById("title").innerHTML = selectedSong.songName;
    masterPlay.classList.remove("bi-play-fill");
    masterPlay.classList.add("bi-pause-fill");
  }
}

function getShuffle() {
  index = Math.floor(Math.random() * song.length);
  playSong(index); // Play a random song
}