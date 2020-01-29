# SDL2
```
#include <SDL2/SDL.h>
#include <iostream>
using namespace std;

int main(){
    int width=512, height=512;
    SDL_Window *window=SDL_CreateWindow("Window",SDL_WINDOWPOS_CENTERED,SDL_WINDOWPOS_CENTERED, width, height, SDL_WINDOW_RESIZABLE);

    if(window==NULL)
        cout << "Error: " << SDL_GetError << endl;

    SDL_Event event;
    bool running=true;

    SDL_Surface *imageSurface=SDL_LoadBMP("image.bmp");

    while(running){
        while(SDL_PollEvent(&event)){
            if(event.type==SDL_QUIT){
                running=false;
                break;
            }
        }

        SDL_Surface *surface=SDL_GetWindowSurface(window);
        Uint32 skyblue=SDL_MapRGB(surface->format, 65, 193, 193);
        SDL_FillRect(surface, NULL, skyblue);
        SDL_BlitSurface( imageSurface, NULL, surface, NULL );
        SDL_UpdateWindowSurface(window);
    }

    SDL_Quit();
    return 0;
}
```
