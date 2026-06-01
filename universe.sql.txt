--
-- PostgreSQL database dump
--

-- Dumped from database version 12.22 (Ubuntu 12.22-0ubuntu0.20.04.4)
-- Dumped by pg_dump version 12.22 (Ubuntu 12.22-0ubuntu0.20.04.4)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: postgres
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO postgres;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: comet; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.comet (
    comet_id integer NOT NULL,
    name character varying(100) NOT NULL,
    galaxy_id integer NOT NULL,
    description text,
    age_in_millions_of_years integer,
    is_spherical boolean NOT NULL
);


ALTER TABLE public.comet OWNER TO postgres;

--
-- Name: comet_comet_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.comet_comet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.comet_comet_id_seq OWNER TO postgres;

--
-- Name: comet_comet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.comet_comet_id_seq OWNED BY public.comet.comet_id;


--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(100) NOT NULL,
    description text,
    age_in_millions_of_years integer,
    distance_from_earth numeric(10,2),
    is_spherical boolean NOT NULL,
    has_life boolean NOT NULL
);


ALTER TABLE public.galaxy OWNER TO postgres;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO postgres;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(100) NOT NULL,
    planet_id integer NOT NULL,
    age_in_millions_of_years integer,
    distance_from_earth numeric(10,2),
    is_spherical boolean NOT NULL,
    has_life boolean NOT NULL
);


ALTER TABLE public.moon OWNER TO postgres;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO postgres;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: planet; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(100) NOT NULL,
    star_id integer NOT NULL,
    age_in_millions_of_years integer,
    distance_from_earth numeric(10,2),
    is_spherical boolean NOT NULL,
    has_life boolean NOT NULL,
    planet_type character varying(50)
);


ALTER TABLE public.planet OWNER TO postgres;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO postgres;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: postgres
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(100) NOT NULL,
    galaxy_id integer NOT NULL,
    age_in_millions_of_years integer,
    distance_from_earth numeric(10,2),
    is_spherical boolean NOT NULL,
    has_life boolean NOT NULL
);


ALTER TABLE public.star OWNER TO postgres;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: postgres
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO postgres;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: postgres
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: comet comet_id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.comet ALTER COLUMN comet_id SET DEFAULT nextval('public.comet_comet_id_seq'::regclass);


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: comet; Type: TABLE DATA; Schema: public; Owner: postgres
--

INSERT INTO public.comet VALUES (1, 'Halley', 1, 'Famous periodic comet visible from Earth every 75 years', 4500, false);
INSERT INTO public.comet VALUES (2, 'Hale-Bopp', 1, 'Great Comet of 1997, one of the most widely observed', 4500, false);
INSERT INTO public.comet VALUES (3, 'Shoemaker-Levy 9', 1, 'Comet that collided with Jupiter in 1994', 4500, false);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: postgres
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 'Our home galaxy, a barred spiral galaxy', 13600, 0.00, false, true);
INSERT INTO public.galaxy VALUES (2, 'Andromeda', 'Nearest spiral galaxy to the Milky Way', 10000, 2537000.00, false, false);
INSERT INTO public.galaxy VALUES (3, 'Triangulum', 'Third-largest galaxy in the Local Group', 10000, 2730000.00, false, false);
INSERT INTO public.galaxy VALUES (4, 'Whirlpool', 'Classic example of a grand-design spiral galaxy', 400, 23000000.00, false, false);
INSERT INTO public.galaxy VALUES (5, 'Sombrero', 'Unbarred spiral galaxy with a bright nucleus', 13250, 29350000.00, false, false);
INSERT INTO public.galaxy VALUES (6, 'Centaurus A', 'Nearest radio galaxy to Earth', 13270, 13000000.00, true, false);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: postgres
--

INSERT INTO public.moon VALUES (1, 'Moon', 1, 4500, 0.00, true, false);
INSERT INTO public.moon VALUES (2, 'Phobos', 2, 4500, 1.00, false, false);
INSERT INTO public.moon VALUES (3, 'Deimos', 2, 4500, 1.00, false, false);
INSERT INTO public.moon VALUES (4, 'Io', 3, 4500, 4.00, true, false);
INSERT INTO public.moon VALUES (5, 'Europa', 3, 4500, 4.00, true, false);
INSERT INTO public.moon VALUES (6, 'Ganymede', 3, 4500, 4.00, true, false);
INSERT INTO public.moon VALUES (7, 'Callisto', 3, 4500, 4.00, true, false);
INSERT INTO public.moon VALUES (8, 'Titan', 4, 4500, 8.00, true, false);
INSERT INTO public.moon VALUES (9, 'Enceladus', 4, 4500, 8.00, true, false);
INSERT INTO public.moon VALUES (10, 'Mimas', 4, 4500, 8.00, false, false);
INSERT INTO public.moon VALUES (11, 'Dione', 4, 4500, 8.00, true, false);
INSERT INTO public.moon VALUES (12, 'Rhea', 4, 4500, 8.00, true, false);
INSERT INTO public.moon VALUES (13, 'Tethys', 4, 4500, 8.00, true, false);
INSERT INTO public.moon VALUES (14, 'Hyperion', 4, 4500, 8.00, false, false);
INSERT INTO public.moon VALUES (15, 'Triton', 8, 4500, 29.00, true, false);
INSERT INTO public.moon VALUES (16, 'Nereid', 8, 4500, 29.00, false, false);
INSERT INTO public.moon VALUES (17, 'Oberon', 7, 4500, 18.00, true, false);
INSERT INTO public.moon VALUES (18, 'Titania', 7, 4500, 18.00, true, false);
INSERT INTO public.moon VALUES (19, 'Ariel', 7, 4500, 18.00, true, false);
INSERT INTO public.moon VALUES (20, 'Umbriel', 7, 4500, 18.00, true, false);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: postgres
--

INSERT INTO public.planet VALUES (1, 'Earth', 1, 4500, 0.00, true, true, 'Terrestrial');
INSERT INTO public.planet VALUES (2, 'Mars', 1, 4500, 1.00, true, false, 'Terrestrial');
INSERT INTO public.planet VALUES (3, 'Jupiter', 1, 4500, 4.00, true, false, 'Gas Giant');
INSERT INTO public.planet VALUES (4, 'Saturn', 1, 4500, 8.00, true, false, 'Gas Giant');
INSERT INTO public.planet VALUES (5, 'Venus', 1, 4500, 0.00, true, false, 'Terrestrial');
INSERT INTO public.planet VALUES (6, 'Mercury', 1, 4500, 0.00, true, false, 'Terrestrial');
INSERT INTO public.planet VALUES (7, 'Uranus', 1, 4500, 18.00, true, false, 'Ice Giant');
INSERT INTO public.planet VALUES (8, 'Neptune', 1, 4500, 29.00, true, false, 'Ice Giant');
INSERT INTO public.planet VALUES (9, 'Proxima b', 2, 4850, 4.00, true, false, 'Terrestrial');
INSERT INTO public.planet VALUES (10, 'Proxima c', 2, 4850, 4.00, true, false, 'Super Earth');
INSERT INTO public.planet VALUES (11, 'Alpha Centauri Ab', 3, 5300, 4.00, true, false, 'Terrestrial');
INSERT INTO public.planet VALUES (12, 'Sirius b', 4, 250, 9.00, false, false, 'Dwarf');


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: postgres
--

INSERT INTO public.star VALUES (1, 'Sun', 1, 4600, 0.00, true, true);
INSERT INTO public.star VALUES (2, 'Proxima Centauri', 1, 4850, 4.00, true, false);
INSERT INTO public.star VALUES (3, 'Alpha Centauri A', 1, 5300, 4.00, true, false);
INSERT INTO public.star VALUES (4, 'Sirius', 1, 250, 9.00, true, false);
INSERT INTO public.star VALUES (5, 'Betelgeuse', 1, 8, 700.00, true, false);
INSERT INTO public.star VALUES (6, 'Vega', 1, 455, 25.00, true, false);


--
-- Name: comet_comet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.comet_comet_id_seq', 3, true);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 6, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 20, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 12, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: postgres
--

SELECT pg_catalog.setval('public.star_star_id_seq', 6, true);


--
-- Name: comet comet_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.comet
    ADD CONSTRAINT comet_name_key UNIQUE (name);


--
-- Name: comet comet_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.comet
    ADD CONSTRAINT comet_pkey PRIMARY KEY (comet_id);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: comet comet_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.comet
    ADD CONSTRAINT comet_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: postgres
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--
