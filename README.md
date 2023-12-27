# Pwndocker

## Versions
[22.04](/pwn/22.04)  
~~20.04~~ 예정  
~~18.04~~ 예정  
~~16.04~~ 예정   

## Feature
- [basic environment](https://github.com/h1ghl1kh7/tools)

## useful commands
1. pull images  
`docker pull h1ghl1kh7/pwn:22.04`
2. run docker  
`docker run -cap-add=SYS_PTRACE --security-opt seccomp=unconfined -d privileged --name pwn22 -v ~/ctf/:/root/ -it h1ghl1kh7/pwn:22.04 /bin/zsh`
3. start docker  
`docker start pwn22`
4. exec docker  
`docker exec --privileged -it pwn22`

## Included Programs
- zsh
   - oh-my-zsh
   - zsh-autosuggestion
   - zsh-syntax-highlighting
   - powerlevel10k
- python3
    - ropper
    - angr
    - z3-solver
    - pwntools
    - ROPgadget
    - capstone
- checksec
- one\_gadget
- vim
    - coc.nvim
        - code snippets
        - coc settings
    - vim-floaterm
    - custom analysis highlight  
        use `// A: ????` -> bg purple, fg black highlight
- gdb-gef

