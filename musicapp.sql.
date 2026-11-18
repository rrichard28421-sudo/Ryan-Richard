-- BANCO DE DADOS DO APLICATIVO DE MÚSICA

CREATE TABLE usuarios (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(150) UNIQUE NOT NULL,
    senha_hash TEXT NOT NULL,
    criado_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE artistas (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(150) NOT NULL,
    biografia TEXT,
    imagem_url TEXT
);

CREATE TABLE albuns (
    id BIGSERIAL PRIMARY KEY,
    nome VARCHAR(150) NOT NULL,
    artista_id BIGINT REFERENCES artistas(id),
    lancamento DATE,
    capa_url TEXT
);

CREATE TABLE musicas (
    id BIGSERIAL PRIMARY KEY,
    titulo VARCHAR(150) NOT NULL,
    album_id BIGINT REFERENCES albuns(id),
    artista_id BIGINT REFERENCES artistas(id),
    duracao_segundos INTEGER,
    audio_url TEXT NOT NULL,
    capa_url TEXT
);

CREATE TABLE playlists (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT REFERENCES usuarios(id),
    nome VARCHAR(100) NOT NULL,
    criada_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE playlist_musicas (
    playlist_id BIGINT REFERENCES playlists(id),
    musica_id BIGINT REFERENCES musicas(id),
    PRIMARY KEY (playlist_id, musica_id)
);

CREATE TABLE favoritos (
    usuario_id BIGINT REFERENCES usuarios(id),
    musica_id BIGINT REFERENCES musicas(id),
    PRIMARY KEY (usuario_id, musica_id)
);

CREATE TABLE historico (
    id BIGSERIAL PRIMARY KEY,
    usuario_id BIGINT REFERENCES usuarios(id),
    musica_id BIGINT REFERENCES musicas(id),
    reproduzida_em TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
