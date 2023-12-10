# Population
#include <stdio.h>

// Define a structure to represent demographic data
struct DemographicData {
    double birthRate;
    double deathRate;
    double migrationRate;
};

// Function to project population for one year based on demographic data
double projectPopulation(double currentPopulation, struct DemographicData demographic) {
    // Project population using a more nuanced model (e.g., accounting for age groups)
    double birthIncrease = currentPopulation * demographic.birthRate;
    double deathDecrease = currentPopulation * demographic.deathRate;
    double migrationChange = currentPopulation * demographic.migrationRate;

    // Adjust the population based on demographic factors
    double projectedPopulation = currentPopulation + birthIncrease - deathDecrease + migrationChange;

    // Ensure the projected population is non-negative
    if (projectedPopulation < 0) {
        projectedPopulation = 0;
    }

    return projectedPopulation;
}

int main() {
    // Initial population for Armenia
    double armeniaPopulation = 3000000;

    // Define demographic data (values are placeholders)
    struct DemographicData armeniaDemographics = {0.01, 0.005, 0.002};

    // Project population for the next 100 years
    for (int year = 1; year <= 100; year++) {
        armeniaPopulation = projectPopulation(armeniaPopulation, armeniaDemographics);

        // Print the projected population for each year
        printf("Year %d: Projected Population = %.0f\n", year, armeniaPopulation);
    }

    return 0;
}
