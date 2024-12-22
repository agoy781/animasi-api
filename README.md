import pygame
import random

pygame.init()

# Ukuran layar
screen_width = 400
screen_height = 300
screen = pygame.display.set_mode((screen_width, screen_height))

# Warna api
colors = [(255, 0, 0), (255, 128, 0), (255, 255, 0)]

# Daftar partikel api
particles = []

# Fungsi untuk membuat partikel baru
def create_particle():
    x = random.randint(0, screen_width)
    y = screen_height
    size = random.randint(5, 10)
    speed = random.randint(1, 3)
    color = random.choice(colors)
    particle = [x, y, size, speed, color]
    particles.append(particle)

# Loop utama
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Membuat partikel baru
    create_particle()

    # Memperbarui posisi partikel
    for particle in particles:
        particle[1] -= particle[3]
        particle[2] -= 0.1  # Mengurangi ukuran partikel

    # Menghapus partikel yang sudah habis
    particles = [particle for particle in particles if particle[2] > 0]

    # Menggambar latar belakang
    screen.fill((0, 0, 0))

    # Menggambar partikel
    for particle in particles:
        pygame.draw.circle(screen, particle[4], (int(particle[0]), int(particle_1)), int(particle[2]))

    pygame.display.update()

pygame.quit()
