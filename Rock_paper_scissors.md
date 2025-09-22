## Завдання виконано на основі здобутих знань, щодо теми VStack,ZStack та UI

import SwiftUI

struct ContentView: View {
    let moves = ["✊", "✋", "✌️"]
    
    @State private var appChoice = Int.random(in: 0...2)
    @State private var shouldWin = Bool.random()
    @State private var score = 0
    @State private var round = 1
    @State private var showingFinalScore = false
    
    var body: some View {
        ZStack {
            RadialGradient(stops: [
                .init(color: Color(red: 0.5, green: 0.1, blue: 0.5), location: 0.3),
                .init(color: Color(red: 0.76, green: 0.15, blue: 0.26), location: 0.3),
            ], center: .top, startRadius: 500, endRadius: 700)
            .ignoresSafeArea()
            
            VStack(spacing: 30) {
                Text("Score: \(score)")
                    .font(.largeTitle.bold())
                    .foregroundStyle(.white)
                
                Text("App’s move:")
                    .font(.headline)
                    .foregroundStyle(.white)
                    
                Text(moves[appChoice])
                    .font(.system(size: 100))
                    
                
                if shouldWin {
                    Text("You must WIN!")
                        .font(.headline)
                        .foregroundStyle(.white)
                } else {
                    Text("You must LOSE!")
                        .font(.headline)
                        .foregroundStyle(.white)
                }

                HStack(spacing: 30) {
                    ForEach(moves.indices, id: \.self) { number in
                        Button(action: {
                            playerTapped(number)
                        }) {
                            Text(moves[number])
                                .font(.system(size: 80))
                        }
                    }
                }
            }
            .padding(.vertical, 20)
            .background(.regularMaterial)
            .clipShape(.rect(cornerRadius: 50))
            .alert("Game Over", isPresented: $showingFinalScore) {
                Button("Play again", action: resetGame)
                    .foregroundStyle(.white)
            } message: {
                Text("Your final score was \(score)")
                    .foregroundStyle(.white)
            }
            .padding()
        }
    }
        
        func playerTapped(_ playerMove: Int) {
            let winningMoves = [1, 2, 0]
            var playerWasCorrect: Bool
            
            if shouldWin {
                playerWasCorrect = (playerMove == winningMoves[appChoice])
            } else {
                playerWasCorrect = (winningMoves[playerMove] == appChoice)
            }
            
            if playerWasCorrect {
                score += 1
            } else {
                score -= 1
            }
            
            if round >= 10 {
                showingFinalScore = true
            } else {
                round += 1
                appChoice = Int.random(in: 0...2)
                shouldWin.toggle()
            }
        }
        
        func resetGame() {
            score = 0
            round = 1
            appChoice = Int.random(in: 0...2)
            shouldWin = Bool.random()
        }
    }

#Preview {
    ContentView()
}
```
<img width="371" height="791" alt="Знімок екрана 2025-09-22 о 3 20 58 пп" src="https://github.com/user-attachments/assets/8971f5b0-da8c-4119-a3d3-e96a171c8e13" />

