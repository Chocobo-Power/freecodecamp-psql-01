DROP TABLE IF EXISTS galaxy CASCADE;
DROP TABLE IF EXISTS star CASCADE;
DROP TABLE IF EXISTS planet CASCADE;
DROP TABLE IF EXISTS moon CASCADE;
DROP TABLE IF EXISTS faction CASCADE;

CREATE TABLE galaxy(
    galaxy_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    ly_diameter INT NOT NULL,
    billion_stars INT,
    b_years_age NUMERIC(19,3),
    description TEXT
);

CREATE TABLE star(
    star_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    planets INT NOT NULL,
    moons INT,
    b_years_age NUMERIC(19,3),
    description TEXT,
    -- intelligent_life BOOLEAN,
    -- warp_capability BOOLEAN,
    galaxy_id BIGINT REFERENCES galaxy(galaxy_id) NOT NULL
);

CREATE TABLE planet(
    planet_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    moons INT NOT NULL,
    orbit_days INT,
    life BOOLEAN,
    civilization BOOLEAN,
    star_id BIGINT REFERENCES star(star_id) NOT NULL
);

CREATE TABLE moon(
    moon_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    orbit_days INT NOT NULL,
    bases INT,
    planet_id BIGINT REFERENCES planet(planet_id) NOT NULL
);

CREATE TABLE faction(
    faction_id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL UNIQUE,
    type INT NOT NULL,
    population INT,
    planet_id BIGINT REFERENCES planet(planet_id) NOT NULL
);

-- GALAXIES
INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Milky Way', 100000, 100, 13.61, 'A nice place to live!');

INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Andromeda', 220000, 1000, 10.01, 'Our friendly neighbour.');

INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Sagittarius', 10000, 100, 5.50, 'The baby brother.');

INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Vader', 10000, 100, 5.50, 'The baby brother.');

INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Palpatine', 10000, 100, 5.50, 'The baby brother.');

INSERT INTO galaxy(name, ly_diameter, billion_stars, b_years_age, description)
VALUES('Dooku', 10000, 100, 5.50, 'The baby brother.');

-- STARS
INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Sol', 8, 146, 4.571, 'The star where planer Earth is located', 1);

INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Proxima Centauri', 3, 0, 4.853, 'The closest star to the Sun!', 2);

INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Alpha Centauri', 0, 0, 4.853, 'Binary system!', 3);

INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Alpha Beta Game', 0, 0, 4.853, 'Binary system!', 1);

INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Asterion', 0, 0, 4.853, 'Binary system!', 2);

INSERT INTO star(name, planets, moons, b_years_age, description, galaxy_id)
VALUES('Pegaso', 0, 0, 4.853, 'Binary system!', 3);

-- Planets
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Earth', 1, 365, true, true, 1);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Mars', 2, 687, false, false, 1);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Jupiter', 5, 4380, false, false, 1);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Saturn', 9, 10585, false, false, 1);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Venus', 9, 10585, false, false, 2);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Patata', 9, 10585, false, false, 2);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Uranus', 9, 10585, false, false, 2);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Mercury', 9, 10585, false, false, 2);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Carrera', 9, 10585, false, false, 3);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Salty', 9, 10585, false, false, 3);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Diamond', 9, 10585, false, false, 3);
INSERT INTO planet(name, moons, orbit_days, life, civilization, star_id) VALUES('Curry', 9, 10585, false, false, 3);

-- Moons
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Luna', 27, 5, 1);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Encedalus', 100, 10, 4);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Uru', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Pisac', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Ollanta', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Cusco', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Amazonas', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Trujillo', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Tacna', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Coma', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Punto', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Raya', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Westeros', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Essos', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Kalimdor', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Arda', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Valinor', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Prin Prin', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Cosmo', 100, 10, 2);
INSERT INTO moon(name, orbit_days, bases, planet_id) VALUES('Arigato', 100, 10, 2);


-- Factions
INSERT INTO faction(name, type, population, planet_id) VALUES('foo', 2, 13, 1);
INSERT INTO faction(name, type, population, planet_id) VALUES('bar', 1, 234, 2);
INSERT INTO faction(name, type, population, planet_id) VALUES('baz', 4, 576565, 3);
